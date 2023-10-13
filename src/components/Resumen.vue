<template>
    <main>
        <p>{{ labelVisual }}</p>
        <h1>{{ amountCurrency }}</h1>
        <div class="graphic">
            <slot name="graphic"></slot>
        </div>
        <div class="actions">
            <slot name="actions"></slot>
        </div>
    </main>
</template>

<script>

    const currencyFormatter = new Intl.NumberFormat('es-CO', { 
        style: 'currency', currency: 'COP' });
    
    export default {
        name: "Resumen",
        props: {
            totalLabel: {
                type: String,
            },
            label: {
                type: String,
            },
            totalAmount: {
                type: Number,
            },
            amount: {
                type: Number,
                default: null
            }
        },
        computed: {
            amountVisual() {
                return this.amount !== null ? this.amount : this.totalAmount;
            },
            labelVisual() {
                return this.amount !== null ? this.label : this.totalLabel;
            },
            amountCurrency() {
                return currencyFormatter.format(this.amountVisual);
            },
        }
    }
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}
h1,
p {
  margin: 0;
  text-align: center;
}
h1 {
  margin-top: 14px;
  color: var(--brand-green);
}
.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>