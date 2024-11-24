<script setup>
import { Tag } from 'ant-design-vue';
const props = defineProps({
    status: {
        type: String,
        default: "none"
    }
})
</script>
<template>
    <Tag :bordered="false" v-if="props.status === 'translate'">Translate</Tag>
    <Tag :bordered="false" v-else-if="props.status === 'calc'">Calculate</Tag>
    <Tag :bordered="false" v-else-if="props.status === 'wiki'">Search in Wiki</Tag>
    <Tag :bordered="false" v-else-if="props.status === 'todo'">Todo</Tag>
</template>
<style scoped>
</style>