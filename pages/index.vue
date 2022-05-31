<template>
<div>
  <Title />
  {{page}}
</div>
</template>

<script>
import {  createClient } from '@/plugins/contentful'
const client = createClient();

export default {
    name: "IndexPage",
    data() {
        return {
            page: []
        };
    },
    mounted() {
        this.getPosts();
    },
    methods: {
        async getPosts() {
            await client.getEntries({
                content_type: 'page'
            })
                .then(response => {
                  console.log(response)
                });
        }
    },
}
</script>
