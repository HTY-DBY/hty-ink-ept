<template>
  <router-view/>
</template>

<script>
import {defineComponent} from 'vue'

export default defineComponent({
  name: 'App'
})
</script>
<script setup>
import {inject, provide, ref} from 'vue'
import {useQuasar} from "quasar";

provide(/* 注入名 */ 'Input_value', /* 值 */ ref(null))
provide(/* 注入名 */ 'Input_unit', /* 值 */ ref('mV'))
provide(/* 注入名 */ 'Input_type', /* 值 */ ref('SHE, Standard Hydrogen Electrode'))

const $q = useQuasar()

// 设置暗色模式状态
$q.dark.set(true) // or false or "auto"


</script>
