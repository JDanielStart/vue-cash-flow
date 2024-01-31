<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <Layout>
        <template #header>
            <Header/>
        </template>
    </Layout>
</template>

<script>
    import Layout from './layout.vue';
    import Header from './Header.vue';

    export default {
        components: {
            Layout,
            Header
}
    }
</script>