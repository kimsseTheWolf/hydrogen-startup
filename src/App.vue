<script setup>
import SearchBar from './components/SearchBar.vue';
import { ConfigProvider, theme } from 'ant-design-vue';
</script>
<template>
    <ConfigProvider :theme="{
        algorithm: theme.darkAlgorithm
    }">
        <SearchBar/>
    </ConfigProvider>
</template>
<style>
html {
    height: 100% !important;
}

body {
    height: 100% !important;
    background-color: rgb(26, 26, 26);
}

#app {
    height: 100% !important;
}
</style>