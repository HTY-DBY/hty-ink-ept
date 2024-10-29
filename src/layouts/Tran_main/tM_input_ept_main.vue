<template>
  <div class="container">
    <div class="item left">
      <div class="ept_input_item_left">
        <div class="text_1">电位数值</div>
        <q-input rounded outlined clearable v-model=Input_value></q-input>
      </div>
      <div class="ept_input_item_right">
        <div class="text_1">单位</div>
        <q-select v-model="Input_unit" :options="unit_options"/>
      </div>

    </div>
    <div class="item right">
      <!--<div class="row">-->
      <div class="text_1">
        参比电极
      </div>
      <q-select v-model="Input_type" :options="type_options"/>
    </div>
  </div>

</template>

<script setup>
import {ref} from "vue";
import Tran_ept_main from "layouts/Tran_main/tM_input_ept_main.vue";
import {ept_dataStorage} from 'app/public/dataStorage';
import {inject} from 'vue'

const Input_value = inject('Input_value')
const Input_unit = inject('Input_unit')
const Input_type = inject('Input_type')

let unit_options = ['V', 'mV']
let type_options = ref(Object.keys(ept_dataStorage))
</script>


<style scoped lang="scss">
.text_1 {
  display: flex;
  justify-content: center;
  padding: 0 0 10px 0;
}

.ept_input_item_left {
  padding: 0 10px 0 0;
  width: 75%;

}

.ept_input_item_right {
  padding: 0 0 0 10px;
  width: 25%;
}

.container {
  display: flex;
  flex-wrap: wrap;

}

.item {
  flex: 1 1 50%; /* Grow and shrink as needed, base width 50% */
  box-sizing: border-box;
  padding: 10px;
}

.item.left {
  display: flex;
  //background-color: lightblue;
}

.item.right {
  //background-color: lightcoral;
}

:deep(.q-field__native, .q-field__input) {
  text-align: center;
}

@media (max-width: 750px) {
  .item {
    flex: 1 1 100%; /* Full width for smaller screens */
  }
}
</style>
