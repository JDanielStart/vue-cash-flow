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
                    <Action/>
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
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
                amounts: [100, 200, 500, 200, -400, -600, -300, 0, 300, 500],
                label: null,
                movements: [
                    {
                        id: 0,
                        title: "Movimiento 1",
                        description: "Lorem ipsum dolor sit",
                        amount: -120,
                    },
                    {
                        id: 1,
                        title: "Movimiento 2",
                        description: "Lorem ipsum dolor sit",
                        amount: 1000,
                    },{
                        id: 2,
                        title: "Movimiento 3",
                        description: "Lorem ipsum dolor sit",
                        amount: 0,
                    },
                    {
                        id: 3,
                        title: "Movimiento 4",
                        description: "Lorem ipsum dolor sit",
                        amount: 1000,
                    },
                    {
                        id: 4,
                        title: "Movimiento 5",
                        description: "Lorem ipsum dolor sit",
                        amount: -183,
                    },
                    {
                        id: 5,
                        title: "Movimiento 6",
                        description: "Lorem ipsum dolor sit",
                        amount: 1000,
                    },
                    {
                        id: 6,
                        title: "Movimiento 7",
                        description: "Lorem ipsum dolor sit",
                        amount: 1000,
                    },
                    {
                        id: 7,
                        title: "Movimiento 8",
                        description: "Lorem ipsum dolor sit",
                        amount: 1000,
                    },
                    {
                        id: 8,
                        title: "Movimiento 9",
                        description: "Lorem ipsum dolor sit",
                        amount: 1000,
                    },
                    {
                        id: 9,
                        title: "Movimiento 10",
                        description: "Lorem ipsum dolor sit",
                        amount: 1000,
                    }
                ]
            }
        }
    }
</script>