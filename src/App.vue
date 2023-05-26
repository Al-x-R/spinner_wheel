<template>
  <div class="wrapper">
    <button class="spin-btn" @click="launchWheel">Spin</button>
    <SingleWheel
      class="wheel"
      :gift="gift"
      ref="wheel"
      v-model="data"
      @done="done"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import SingleWheel from '@/components/SingleWheel.vue';

const wheel = ref(null);
const data = ref([
  {
    id: 1,
    value: 'Gift 1',
    bgColor: '#7d7db3',
    color: '#ffffff',
  },
  {
    id: 2,
    value: 'Gift 2',
    bgColor: '#ffffff',
    color: '#000000',
  },
  {
    id: 3,
    value: 'Gift 3',
    bgColor: '#c92729',
    color: '#ffffff',
  },
  {
    id: 4,
    value: 'Gift 4',
    bgColor: '#7d7db3',
    color: '#ffffff',
  },
  {
    id: 5,
    value: 'Gift 5',
    bgColor: '#ffffff',
    color: '#000000',
  },
  {
    id: 6,
    value: 'Gift 6',
    bgColor: '#c92729',
    color: '#ffffff',
  },
]);
const gift = ref(0);

const launchWheel = () => {
  const randomIndex = Math.floor(Math.random() * data.value.length);
  gift.value = randomIndex + 1;

  setTimeout(() => {
    wheel.value.spin();
  }, 100);
};
const done = (r) => {
  alert(`Win ${ r.value }`);
};

</script>

<style scoped lang="scss">

.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;

  .spin-btn {
    padding: 11px 57px;
    color: white;
    background-color: purple;
    border-radius: 10px;
    align-self: flex-start;
  }
}

</style>
