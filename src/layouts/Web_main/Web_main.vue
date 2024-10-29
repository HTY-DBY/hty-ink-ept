<template>
  <div class="container">
    <div class="item left">
      <Imformation_main></Imformation_main>
    </div>
    <div class="item right">
      <Tran_main></Tran_main>
    </div>
  </div>
</template>

<script setup>
import Imformation_main from "layouts/Web_main/Imformation_main/Imformation_main.vue";
import Tran_main from "layouts/Tran_main/Tran_main.vue";
</script>

<style scoped lang="scss">
.container {
  display: flex;
  flex-wrap: nowrap; /* Prevent wrapping */
}

.item {
  box-sizing: border-box;
  padding: 20px;
}

.item.left {
  flex: 1 1 30%; /* Set left item width to 30% */
}

.item.right {
  flex: 1 1 70%; /* Set right item width to 70% */
}

@media (max-width: 750px) {
  .container {
    flex-wrap: wrap-reverse; /* Allow children to wrap to the next line and reverse the order */
  }

  .item.left {
    flex: 1 1 100%; /* Set left item width to 100% */
    //background-color: lightblue;
  }

  .item.right {
    flex: 1 1 100%; /* Set right item width to 100% */
    //background-color: lightcoral;
  }
}
</style>
