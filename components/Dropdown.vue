<template>
    <div class="form-group">
            <label for="country">{{dropdownData}}</label>
        </div>
</template>

<script>
    import {  createClient } from '@/plugins/contentful'
    const client = createClient();

    export default {
        name: "dropdownComponent",
        data() {
            return {
                dropdownData : []
            };
        },
        mounted() {
            console.log(this.getPosts());
        },
        methods: {
            async getPosts() {
                await client.getEntry('4prKyCBmEikaFurk1mlWT0')
                    .then(function (entry) {
                        console.log(entry.fields.title);
                        this.dropdownData  = entry.fields.label
                    });
            }
        },
    }
</script>
