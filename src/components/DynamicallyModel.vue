<script setup lang="ts">
import { computed, ref } from 'vue'

const input1 = ref<string>('')
const input2 = ref<string>('')
const checkbox = ref<boolean>(false)

const secondInputValue = computed({
  get: () => (checkbox.value ? input1.value : input2.value),
  set: (val: string) => {
    if (checkbox.value) {
      input1.value = val
    } else {
      input2.value = val
    }
  },
})
</script>

<template>
  <section class="m-4">
    <div class="card shadow-xl w-96">
      <div class="card-body space-y-4">
        <div class="card-title flex justify-between">
          <h3>Dynamically Model</h3>
          <input class="checkbox" type="checkbox" v-model="checkbox" />
        </div>

        <div class="flex flex-col gap-4">
          <input class="input" type="text" placeholder="input1" v-model="input1" />
          <input
            class="input"
            type="text"
            placeholder="input2"
            v-model="secondInputValue"
            :disabled="checkbox"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped></style>
