<template>
<div>
  <Title />
</div>
</template>

<script>
import {  createClient } from '@/plugins/contentful'
const client = createClient();

export default {
    name: "IndexPage",
    data() {
        return {
            page: [],
            assets: []
        };
    },
    mounted() {
        this.getPosts();
    },
    methods: {
        async getPosts() {
            await client.getEntry('oBzgoVONtgfjTCn1sTpWJ')
                .then(response => {
                    console.log(response);
                });
        }
    },
}
</script>
