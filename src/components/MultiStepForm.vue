<template>
  <div id="app" class="flex flex-col items-center justify-center min-h-screen bg-gray-100">
    <div class="bg-white p-8 rounded shadow-md w-full max-w-md">
      <div class="flex justify-between items-center mb-8">
        <div class="flex flex-col items-center">
          <div :class="['w-8 h-8 rounded-full flex items-center justify-center', currentStep > 1 ? 'bg-gray-300 text-white' : 'bg-black text-white']">
            <span>1</span>
          </div>
          <span class="text-sm mt-2 text-gray-600">Personal Information</span>
        </div>
        <div class="flex flex-col items-center">
          <div :class="['w-8 h-8 rounded-full flex items-center justify-center', currentStep === 2 ? 'bg-black text-white' : 'bg-gray-300 text-white']">
            <span>2</span>
          </div>
          <span class="text-sm mt-2 text-gray-600">Additional Information</span>
        </div>
      </div>
      <div class="border-b border-gray-200 mb-8"></div>
      <form @submit.prevent="nextStep">
        <div v-if="currentStep === 1">
          <h2 class="text-lg font-medium mb-4">Personal Information</h2>
          <p class="text-sm text-gray-600 mb-4">Please fill out your personal information</p>
          <div class="mb-4">
            <label class="block text-gray-700 text-sm font-medium mb-2">Name</label>
            <input type="text" v-model="formData.name" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="Enter your name" required />
          </div>
          <div class="mb-4">
            <label class="block text-gray-700 text-sm font-medium mb-2">Gender</label>
            <div class="flex items-center">
              <label class="mr-4">
                <input type="radio" v-model="formData.gender" value="male" required />
                <span class="ml-2">Male</span>
              </label>
              <label class="mr-4">
                <input type="radio" v-model="formData.gender" value="female" required />
                <span class="ml-2">Female</span>
              </label>
              <label>
                <input type="radio" v-model="formData.gender" value="other" required />
                <span class="ml-2">Other</span>
              </label>
            </div>
          </div>
        </div>
        <div v-if="currentStep === 2">
          <h2 class="text-lg font-medium mb-4">Additional Information</h2>
          <p class="text-sm text-gray-600 mb-4">Please provide additional details</p>
          <div class="mb-4">
            <label class="block text-gray-700 text-sm font-medium mb-2">Description</label>
            <textarea v-model="formData.description" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="Enter a description"></textarea>
          </div>
          <div class="mb-4">
            <label class="block text-gray-700 text-sm font-medium mb-2">Title</label>
            <input type="text" v-model="formData.title" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="Enter a title" list="title-options" required />
            <datalist id="title-options">
              <option v-for="option in titleOptions" :key="option" :value="option">{{ option }}</option>
            </datalist>
          </div>
        </div>
        <div class="flex justify-between items-center">
          <button type="button" @click="prevStep" v-if="currentStep > 1" class="px-4 py-2 bg-gray-300 text-gray-700 rounded">Back</button>
          <button type="submit" class="px-4 py-2 bg-black text-white rounded">{{ currentStep === 2 ? 'Submit' : 'Next' }}</button>
        </div>
      </form>
      <div class="mt-8">
        <div class="relative pt-1">
          <div class="flex mb-2 items-center justify-between">
            <div>
              <span class="text-xs font-semibold inline-block py-1 px-2 uppercase rounded-full text-black bg-gray-300">
                {{ progress }}%
              </span>
            </div>
          </div>
          <div class="overflow-hidden h-2 mb-4 text-xs flex rounded bg-gray-200">
            <div :style="{ width: progress + '%' }" class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-black"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

interface FormData {
  name: string;
  gender: string;
  description: string;
  title: string;
}

const currentStep = ref<number>(1);
const formData = ref<FormData>({
  name: '',
  gender: '',
  description: '',
  title: ''
});
const titleOptions = ref<string[]>(["Mr.", "Mrs.", "Ms.", "Dr.", "Prof."]);

const nextStep = () => {
  if (currentStep.value < 2) {
    currentStep.value++;
  } else {
    alert('Form submitted!');
  }
};

const prevStep = () => {
  if (currentStep.value > 1) {
    currentStep.value--;
  }
};

const progress = computed<number>(() => {
  return (currentStep.value / 2) * 100;
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap');
body {
  font-family: 'Roboto', sans-serif;
}
</style>
