<template>
    
    <div>
        This is projects from Projects Component!

        <br>
        Title: {{ title }}
        <br>
        Id: {{ id }}

        <button @click="$emit('increase-size')">Enlarge Text</button>

        <button>This is another button</button>


        <!-- Default SLOT -->
        <button>  <slot></slot> </button>

        <!-- Named SLOT -->
        <footer> <slot name="footer"> </slot>
        </footer>
        
    </div>


</template>

<script setup>
const props = defineProps({
    title: String,
    id: Number
})
</script>


<style scoped>
div {
  width: 100%;
  height: 200px;
  border-style: solid;
}
</style>