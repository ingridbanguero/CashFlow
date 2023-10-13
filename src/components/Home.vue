<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resumen
                :total-label="'Monto total'"
                :label="label"
                :total-amount="1000000"
                :amount="amount"
            >
                <template #graphic>
                    <Graphic :amounts="amounts" />
                </template>

                <template #actions>
                    <Action/>
                </template>
            </Resumen>
        </template>
        <template #movements>
            <Movements
                :movements="movements"
            
            />
        </template>
    </Layout>
</template>


<script>
    import Layout from "@/components/Layout.vue";
    import Header from "@/components/Header.vue";
    import Resumen from "@/components/Resumen.vue";
    import Movements from "@/components/Movements.vue";
    import Action from "./Action.vue";
    import Graphic from "./Graphic.vue";

    export default {
        name: "Home",
        components: {
            Layout,
            Header,
            Resumen,
            Movements,
            Action,
            Graphic,
        },
        data() {
            return {
                amount: null,
                label: null,
                amounts: [100, 200, 500, 200, -400, -600, -300, 0, 300, 500],
                movements: [
                    {
                        id: 1,
                        title: "Movimiento 1",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: 1000,
                    },
                    {
                        id: 2,
                        title: "Movimiento 2",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: 2000,
                    },
                    {
                        id: 3,
                        title: "Movimiento 3",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: -3000,
                    },
                    {
                        id: 4,
                        title: "Movimiento 4",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: 1000,
                    },
                    {
                        id: 5,
                        title: "Movimiento 5",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: 2000,
                    },
                    {
                        id: 6,
                        title: "Movimiento 6",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: 3000,
                    },
                    {
                        id: 7,
                        title: "Movimiento 7",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: 1000,
                    },
                    {
                        id: 8,
                        title: "Movimiento 8",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: 2000,
                    },
                    {
                        id: 9,
                        title: "Movimiento 9",
                        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
                        amount: 3000,
                    }
            
                ], 
                
            }
        },
    }
</script>