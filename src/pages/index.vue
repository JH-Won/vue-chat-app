<script setup>
import { ref, watch } from 'vue';
import axios from 'axios';
import AiTextBox from '@/components/AiTextBox.vue';
import UserTextBox from '@/components/UserTextBox.vue';

const userChatHistory = ref([])
const aiChatHistory = ref([])
const aiResponse = ref('')

const onQuerySubmitted = async (value) => {
  userChatHistory.value.push(value)
  const ret = genAIAPIcall(value)
  aiChatHistory.value.push(ret)
}

const genAIAPIcall = async (query) => {
  console.log(query)
  // try {
  //   const response = await axios.post('some/strem', query, {
  //     headers: {
  //       'Content-Type': 'text/plain',
  //       'responseType': 'stream',
  //     }
  //   });

  //   const reader = response.data.getReader();
  //   const decoder = new TextDecoder();
  //   let result = '';



  // } catch (error) {
  //   console.log('Error : ', error)
  //   aiResponse.value = "에러 발생, 다시 실행해주세요."
  // } 
  return "This is response"
}

</script>

<template>
  <v-container>
    <v-card :elevation="0">
      <v-card-text style="max-height: 800px; overflow-y: auto;">
          <v-row v-for="(userText, index) in userChatHistory" :key="index">
              <v-col cols="12">
                <UserTextBox :isHistory="true" :incomingValue="userText" />
                <AiTextBox :includeCode="false" :incomingValue="aiChatHistory[index]" />
              </v-col>
          </v-row>
      </v-card-text>
    </v-card>

    <v-card color="dark" elavation="10" 
    style="position: fixed; bottom: 0; left: 30px; right: 30px; z-index: 1;">
      <v-card-text>
        <UserTextBox :isHistory="false" @querySubmitted="onQuerySubmitted"/>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<style>
.v-card-text::-webkit-scrollbar {
  display: none;
}
</style>