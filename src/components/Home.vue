<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <Layout>
        <template #header>
            <Header/>
        </template>
        <template #resume>
            <Resume
                :totalLabel="'Ahorro total'"
                :label="label"
                :total-amount="totalAmount"
                :amount="amount"
            >
                <template #graphic>
                    <Graphic :amounts="amounts"/>
                </template>
                <template #action>
                    <Action @create="create"/>
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
                @remove="remove"
            />
        </template>
    </Layout>
</template>

<script>
    import Layout from './layout.vue';
    import Header from './Header.vue';
    import Resume from "./Resume/Index.vue";
    import  Action  from "@/components/Action.vue";
    import Movements from "./Movements/Index.vue";
    import Graphic from './Resume/Graphic.vue';

    export default {
        components: {
            Layout,
            Header,
            Resume,
            Action,
            Movements,
            Graphic,
        },
        data() {
            return {
                amount: null,
                label: null,
                movements: []
            }
        },
        computed: {
            amounts() {
                return this.movements
                .filter(m => {
                    const today = new Date();
                    const oldDate = today.setDate(today.getDay() - 30);

                    return m.time >= oldDate;
                })
                .map(m => m.amount);
            },
            totalAmount() {
                return this.movements.reduce((suma, m) => {
                    return suma + m.amount;
                }, 0);
            }
        },
        mounted() {
            const movements = JSON.parse(localStorage.getItem("movements"));

            if (Array.isArray(movements)) {
                this.movements = movements?.map(m => {
                    return { ...m, time: new Date(m.time) };
                });
            }
        },
        methods: {
            create(movement) {
                this.movements.push(movement);
                this.save();
            },
            remove(id) {
                this.movements = this.movements
                .filter(m => m.id != id);
                this.save();
            },
            save() {
                localStorage.setItem("movements", JSON.stringify(this.movements));
            }
        }
    }
</script>