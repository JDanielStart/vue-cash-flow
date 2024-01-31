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
                graphic
            </template>
            <template #action>
                action
            </template>
            </Resume>
        </template>
    </Layout>
</template>

<script>
    import Layout from './layout.vue';
    import Header from './Header.vue';
    import Resume from "./Resume/index.vue"

    export default {
        components: {
            Layout,
            Header,
            Resume
        },
        data() {
            return {
                amount: null,
                label: null,
            }
        }
    }
</script>