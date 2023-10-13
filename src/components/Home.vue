<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resumen
                :total-label="'Monto total'"
                :label="label"
                :total-amount="totalAmount"
                :amount="amount"
            >
                <template #graphic>
                    <Graphic :amounts="amounts" @select="onSelect"/>
                </template>

                <template #actions>
                    <Action @create="create"/>
                </template>
            </Resumen>
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
                movements: [], 
                
            }
        },
        computed: {
            amounts(){
                const lastDays = this.movements
                .filter(m => {
                    const today = new Date();
                    const oldDate = today.setDate(today.getDate() - 30);
                    return m.time > oldDate;
                })
                .map(m => m.amount)

                return lastDays.map((m, i) => {
                    const lastMovements = lastDays.slice(0, i + 1);
                    return lastMovements.reduce((suma, movement) => {
                        return suma + movement;
                    }, 0)
                })
            },
            totalAmount(){
                return this.movements.reduce((suma, movement) => {
                    return suma + movement.amount;
                }, 0)
            }
        },
        mounted(){
            const movements = JSON.parse(localStorage.getItem("movements")) || [];
            if(Array.isArray(movements)){
                this.movements = movements?.map(m => {
                return {...m, time: new Date(m.time)}
            })
            }
        },
        methods: {
            create(movement){
                this.movements.push(movement);
                this.save();
            },
            remove(id){
                const index = this.movements.findIndex(m => m.id === id);
                this.movements.splice(index, 1);
                this.save();
            },
            save(){
                localStorage.setItem("movements", JSON.stringify(this.movements));
            },
            select(el){
                console.log(el)
                this.amount = el;
            }
        }
    }
</script>