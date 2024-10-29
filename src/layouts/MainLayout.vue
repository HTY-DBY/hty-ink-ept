<template>
  <div>
    <div class="Title_main">
      <Title_main></Title_main>
    </div>
    <!--电位转换main-->
    <div class="Tran_main">
      <web_main></web_main>
    </div>
    <div class="Foot_main">
      <Foot_main></Foot_main>
    </div>
  </div>


</template>

<script setup>
import {ref} from "vue";
import Tran_ept_main from "layouts/Tran_main/tM_input_ept_main.vue";
import Tran_main from "layouts/Tran_main/Tran_main.vue";
import Title_main from "layouts/Title_main/Title_main.vue";
import Foot_main from "layouts/Web_main/Foot_main/Foot_main.vue";
import Imformation_main from "layouts/Web_main/Imformation_main/Imformation_main.vue";
import Web_main from "layouts/Web_main/Web_main.vue";

let options = ['V', 'mV']
let Input_value = ref(null)
let Input_unit = ref('mV')
let Input_type = ref(null)
</script>

<style scoped lang="scss">
.Title_main {
  //border-style: solid;
  //border-color: #15d2e3;
}


.Tran_main {
  //border-style: solid;
  //border-color: red;
  //max-width: 800px;
}

.Foot_main {
  //border-style: solid;
  //border-color: #b60cde;
}
</style>
