<script setup>
import { Flex, Select, SelectOption } from 'ant-design-vue';
import { ref, defineModel } from 'vue';
import { GoogleOutlined, SearchOutlined, PlusCircleOutlined } from "@ant-design/icons-vue"

import SearchBarSmartStatusDisplay from './SearchBarSmartStatusDisplay.vue';

const searchEngine = ref('Bing');
const inputModel = defineModel("value", {
    type: String,
    default: ""
})

// smart-input compactbility ====================
const activeMode = ref("none");

function handleInput() {
    // special commands
    if (inputModel.value.toLowerCase() == "translate: ") {
        activeMode.value = "translate";
        inputModel.value = "";
    }
    else if (inputModel.value.toLowerCase() == "calc: ") {
        activeMode.value = "calc";
        inputModel.value = "";
    }
    else if (inputModel.value.toLowerCase() == "wiki: ") {
        activeMode.value = "wiki";
        inputModel.value = "";
    }
    // search engine commands
    else if (inputModel.value.toLowerCase() == "google: ") {
        searchEngine.value = "Google";
        inputModel.value = "";
    }
    else if (inputModel.value.toLowerCase() == "bing: ") {
        searchEngine.value = "Bing";
        inputModel.value = "";
    }
    else if (inputModel.value.toLowerCase() == "duckduckgo: ") {
        searchEngine.value = "DuckDuckGo";
        inputModel.value = "";
    }
    else if (inputModel.value.toLowerCase() == "todo: ") {
        activeMode.value = "todo";
        inputModel.value = "";
    }
}

function quickModeResetHandler(event) {
    if (event.key === "Backspace" || event.key === "Delete") {
        if (inputModel.value.length == 0) {
            activeMode.value = "none";
        }
    }
    else {
        handleInput();
    }
}
// ===============================================

</script>
<template>

    <Flex vertical gap="small">
        <Flex class="input-box-container" gap="small" align="center">
            <SearchBarSmartStatusDisplay :status="activeMode"/>
            <input v-model="inputModel" type="text" placeholder="Search everything you want..." @keydown="quickModeResetHandler"/>
            <Select v-model:value="searchEngine">
                <SelectOption value="Google">
                    <GoogleOutlined />
                    Google
                </SelectOption>
                <SelectOption value="Bing">
                    <SearchOutlined />
                    Bing
                </SelectOption>
                <SelectOption value="DuckDuckGo">
                    <PlusCircleOutlined />
                    DuckDuckGo
                </SelectOption>
            </Select>
        </Flex>
        <Flex v-if="inputModel.length != 0" vertical gap="small" class="floating-card">
            This is the floating card
        </Flex>
    </Flex>
    
    

</template>
<style scoped>
.input-box-container {
    width: 55%;
    height: fit-content;
    padding: 5px;
    border-radius: 10px;
    background-color: rgba(255, 255, 255, 0.2);
}

.input-box-container input {
    border: none;
    background-color: transparent;
    color: white;
    flex: auto;
    font-size: 16px;
}

.input-box-container input::placeholder {
    color: gray;
}

.input-box-container input:focus {
    outline: none;
}

.floating-card {
    width: 55%;
    height: fit-content;
    padding: 5px;
    border-radius: 10px;
    background-color: rgba(255, 255, 255, 0.2);
}
</style>