<template>
<div>
  <Title />
  <Dropdown/>
</div>
</template>

<script>
import {  createClient } from '@/plugins/contentful'
import Dropdown from '../components/Dropdown.vue';
const client = createClient();

export default {
  components: { Dropdown },
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
