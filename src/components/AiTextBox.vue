<script setup>
import { ref } from 'vue'

const props = defineProps({
    includeCode : Boolean,
    incomingValue : String,
})

const includeCode = props.includeCode
const incomingValue = props.incomingValue
const loading = false;

let inputValue = incomingValue ? incomingValue : ref('') 

let onClickClipBoard = () => {
    
}

</script>

<template>
    <v-textarea 
        v-model="inputValue"
        :loading="loading"
        variant="solo-filled" 
        rows="1"
        row-height="15"
        bg-color='light-blue'
        prepend-inner-icon='mdi-robot'
        readonly
        auto-grow
        >
    </v-textarea>
</template>

  