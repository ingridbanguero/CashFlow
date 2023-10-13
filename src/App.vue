<template>
  <Suspense> <!-- Componente que recibe dos slots -->
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

<script>
  import SplashScreen from "@/components/SplashScreen.vue";
  import Home from "@/components/Home.vue"; 
  import { defineAsyncComponent } from "vue";
  
  // Composition API
  export default {
    name: "App",
    components: {
      SplashScreen,
      Home: defineAsyncComponent(() => 
      new Promise((resolve) => {
        setTimeout(() => {
          resolve(import("@/components/Home.vue"));
        }, 2500);
      })
      ),
    }
  }
</script>

<style>
  .app {
    min-height: 100vh;
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
  }

  * {
    --brand-green: #04b500;
    --brand-blue: #0689b0;
  }
</style>
