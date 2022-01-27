<template>
    <div class="box" :style="{width: value+'%'}">
        
    </div>
</template>
<script>
export default {
    props: {
        value: Number,
    },
}
</script>
<style>
    .box {
        height: 100px;
        background-color: red;
        transition: width 1s ease;
    }
</style>