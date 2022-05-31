<template>
    <div v-if="categories">
        <span 
            v-for="(categorie,index) in categories" 
            :key="index"
            class="text-lg pr-5 text-blue-500"
            >
            {{categorie.fields.title}}
        </span>
    </div>
    <div v-else>
        <span class="text-lg pr-5 text-blue-500"> There is no categories in this blog</span>
    </div>
</template>
<script>
export default{
    props : ['categories']
}

</script>