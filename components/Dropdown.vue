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

const contentful = require('contentful')
const client = contentful.createClient({
	space: process.env.CTF_SPACE_ID,
	accessToken: process.env.CTF_CDA_ACCESS_TOKEN
})
client.getEntry('4prKyCBmEikaFurk1mlWT0').then(function (entry) {
  console.log(entry.fields.label);
  console.log(entry.fields.title);
});


</script>