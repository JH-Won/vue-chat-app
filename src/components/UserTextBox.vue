<script setup>
import { ref,defineEmits } from 'vue'
const props = defineProps({
    isHistory : Boolean,
    incomingValue : String,
})

const emit = defineEmits([
    'querySubmitted'
])

const isHistory = props.isHistory
const incomingValue = props.incomingValue

let inputValue = incomingValue ? incomingValue : ref('') 

let onClick = () => {
    if (isHistory) {
        return;
    }
    emit('querySubmitted', inputValue.value)
    inputValue.value = '';
}
</script>

<template>
    <v-text-field
        v-model="inputValue"
        variant="solo-filled" 
        rows="1"
        row-height="15"
        bg-color="light-dark"
        :placeholder="isHistory ? '' : '무엇이든 질문해보세요'"
        prepend-inner-icon="mdi-account"
        :append-inner-icon="isHistory ? 'null' : 'mdi-arrow-right-bold-circle'"
        @click:append-inner="onClick"
        @keyup.enter="onClick"
        :readonly="isHistory"
        >
    </v-text-field>
</template>