<template>
  <Chart
    type="doughnut"
    :width="width"
    :height="height"
    :data="data"
    :options="options"
  />
</template>

<script>
import { defineComponent, computed } from 'vue'
import { useStore } from '@/store'

export default defineComponent({
  props: {
    width: {
      type: Number,
      default: 0
    },
    height: {
      type: Number,
      default: 0
    }
  },
  setup() {
    const store = useStore()
    const darkMode = computed(() => store.state.main.darkMode)
    const data = computed(() => {
      return {
        labels: ['Html', 'Vuejs', 'Laravel'],
        datasets: [
          {
            data: [15, 10, 65],
            backgroundColor: ['#2BB6D0', '#E63b1f', '#203f90'],
            hoverBackgroundColor: ['#2BB6D0', '#E63b1f', '#203f90'],
            borderWidth: 5,
            borderColor: darkMode.value ? '#303953' : '#fff'
          }
        ]
      }
    })
    const options = computed(() => {
      return {
        cutoutPercentage: 80
      }
    })

    return {
      data,
      options
    }
  }
})
</script>
