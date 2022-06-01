<template>
    <div v-if="showPage">
        <Header :header="page.header" class="max-w-2xl mx-auto"/>
        <div class="bg-green-separator"></div>
        <Banner :banner="page.banner"/>
        <Form :form="page.form"/>
    </div>
</template>

<script>
import {  createClient } from '@/plugins/contentful'
const client = createClient();

export default {
    name: "IndexPage",
    data() {
        return {
            showPage : false,
            page: {
                header : {},
                banner : {},
                form : {}
            },
        };
    },
    mounted() {
        this.getPosts();
    },
    methods: {
        async getPosts() {
            await client.getEntries({
                content_type:'page'
            })
                .then(response => {
                response.items.map( el =>{
                    this.page.header = el.fields.header
                    this.page.banner = el.fields.banner
                    this.page.form = el.fields.form
                    this.showPage = true;
                })
            });
        }
    },
}
</script>
<style>

    body{
        font-family: 'Poppins', sans-serif;
    }

    .bg-green-separator{
        background-color: #96c93d;
        height: 15px;
    }
</style>
