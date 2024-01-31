<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <Layout>
        <template #header>
            <Header/>
        </template>
        <template #resume>
            <Resume/>
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
}
    }
</script>