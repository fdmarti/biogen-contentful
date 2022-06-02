<template>
    <div v-if="showPage">
        <Header :header="page.header" class="max-w-2xl mx-auto"/>
        <div class="bg-green-separator"></div>
        <Banner :banner="page.banner"/>
        <Form :form="page.form"/>
        <Footer :footer="page.footer"/>
        <div class="bg-blue-separator"></div>
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
                form : {},
                footer: {}
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
                    console.log(el.fields)
                    this.page.header = el.fields.header
                    this.page.banner = el.fields.banner
                    this.page.form = el.fields.form
                    this.page.footer = el.fields.footer
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

    .bg-blue-separator{
        background-color: #508197;
        height: 15px;
    }
</style>
