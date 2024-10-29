<template>
  <div class="test1">
    <div v-for="(item, index) in formattedItems" :key="index">
      <div class="Out_b">
        <div class="left_text">
          <q-icon name="filter_b_and_w" size="20px" class="icon_css"/>
          <div class="self-center full-width no-outline" tabindex="0" v-html="item"></div>
        </div>
        <div class="cen_text">
          <div>

          </div>
          <q-input color="primary"
                   class="show_text_main"
                   outlined
                   readonly
                   v-model="dataStorage_now[items[index]]"
          />
          <div>
            mV
          </div>
        </div>
        <!--<q-separator color="orange" inset/>-->
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref, computed, watch} from "vue";
import {ept_dataStorage} from 'app/public/dataStorage';

let dataStorage_now = ref(Object.assign({}, ept_dataStorage))
for (let key in dataStorage_now.value) {
  dataStorage_now.value[key] = null
}

const items = ref(Object.keys(ept_dataStorage))
import {inject} from 'vue'

const Input_value = inject('Input_value')
const Input_unit = inject('Input_unit')
const Input_type = inject('Input_type')

function Cal_main(Input_value) {
  Input_value = parseFloat(Input_value)
  let Cal_input_value = Input_value
  if (Input_unit.value === 'mV') {Cal_input_value = Input_value / 1000}
  // console.log('Input Value: ' + Input_value + ' ' + Input_unit.value)

  for (let key in dataStorage_now.value) {
    console.log(Cal_input_value + ept_dataStorage[key])
    let temp = Cal_input_value + ept_dataStorage[key] - ept_dataStorage[Input_type.value]
    // console.log(temp)
    dataStorage_now.value[key] = temp * 1000
    dataStorage_now.value[key] = parseFloat(dataStorage_now.value[key].toFixed(8))
  }
  // console.log(dataStorage_now.value)
}

// 计算本质
watch(Input_value, (Input_value, oldValue) => {
  Cal_main(Input_value)
})
watch(Input_unit, (a, b) => {
  Cal_main(Input_value.value)
})
watch(Input_type, (a, b) => {
  Cal_main(Input_value.value)
})
// 转换为含有上下标的格式
const formattedItems = computed(() => {
  return items.value.map(item =>
    item
      .replace(/_([a-zA-Z0-9])/g, '<sub>$1</sub>')  // 将_后面的字符转换为下标
      .replace(/\^([a-zA-Z0-9])/g, '<sup>$1</sup>') // 将^后面的字符转换为上标
  );
});
</script>

<style scoped lang="scss">
.test1 {
  //border-style: solid;
  //border-color: #41d520;
  padding: 35px 0 0 0;
}

.left_text {
  display: flex;
  align-items: center;
}

.Out_b {
  padding: 20px 10px 0 10px;
}

.cen_text {
  display: flex;
  justify-content: space-evenly;
  padding: 16px 0 0 0;
  align-items: center;

}

:deep(.q-field__control) {
  //color: var(--q-primary);
  height: 40px;
  //width: 70%;
  //max-width: 100%;
  //outline: none;
}


:deep(.q-field) {
  width: 70%
}

:deep(.q-field__native, .q-field__prefix, .q-field__suffix, .q-field__input) {
  text-align: center;
}

.icon_css {
  padding: 0 10px 0 0;
}
</style>
