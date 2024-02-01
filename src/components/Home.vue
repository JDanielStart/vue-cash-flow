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
                :total-amount="1000000"
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
                movements: [
                    {
                        id: 0,
                        title: "Movimiento 1",
                        description: "Lorem ipsum dolor sit",
                        amount: 300,
                        time: new Date("6/12/2023")
                    },
                    {
                        id: 1,
                        title: "Movimiento 2",
                        description: "Lorem ipsum dolor sit",
                        amount: 0,
                        time: new Date("6/12/2023")
                    },{
                        id: 2,
                        title: "Movimiento 3",
                        description: "Lorem ipsum dolor sit",
                        amount: 0,
                        time: new Date("6/12/2023")
                    },
                    {
                        id: 3,
                        title: "Movimiento 4",
                        description: "Lorem ipsum dolor sit",
                        amount: -400,
                        time: new Date("6/12/2023")
                    },
                    {
                        id: 4,
                        title: "Movimiento 5",
                        description: "Lorem ipsum dolor sit",
                        amount: -600,
                        time: new Date("6/12/2023")
                    },
                    {
                        id: 5,
                        title: "Movimiento 6",
                        description: "Lorem ipsum dolor sit",
                        amount: -380,
                        time: new Date("6/12/2023")
                    },
                    {
                        id: 6,
                        title: "Movimiento 7",
                        description: "Lorem ipsum dolor sit",
                        amount: 0,
                        time: new Date("6/12/2023")
                    },
                    {
                        id: 7,
                        title: "Movimiento 8",
                        description: "Lorem ipsum dolor sit",
                        amount: 300,
                        time: new Date("6/12/2023")
                    },
                    {
                        id: 8,
                        title: "Movimiento 9",
                        description: "Lorem ipsum dolor sit",
                        amount: 500,
                        time: new Date("6/12/2023")
                    },
                    {
                        id: 8,
                        title: "Movimiento 9",
                        description: "Lorem ipsum dolor sit",
                        amount: 500,
                        time: new Date("6/12/2023")
                    },
                ]
            }
        },
        computed: {
            amounts() {
                return this.movements
                .filter(m => {
                    const today = new Date();
                    const oldDate = today.setDate(today.getDay() - 30);

                    return m.time <= oldDate;
                })
                .map(m => m.amount);
            }
        },
        methods: {
            create(movement) {
                this.movements.push(movement);
            },
            remove(id) {
                this.movements = this.movements
                .filter(m => m.id != id);
            }
        }
    }
</script>