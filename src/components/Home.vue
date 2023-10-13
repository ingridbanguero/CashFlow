<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
    </Layout>
</template>


<script>
    import Layout from "@/components/Layout.vue";
    import Header from "./Header.vue";
    export default {
        name: "Home",
        components: {
            Layout,
            Header
        }
    }
</script>