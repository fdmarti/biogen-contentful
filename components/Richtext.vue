<template>
    <div v-if="dataRichtext" class="form-group">
    <section>
        <div v-for="(field, index) in dataRichtext.fields.content.content" :key="index" class="form">

        {{field}}
            <!-- <a :href="field.data.uri" target="_blank" v-if="field.data.uri">{{field.data.uri}}</a>
            {{field.value}} -->
        </div>
    </section>
    </div>
</template>
<script>
export default {
    props: ["dataRichtext"]
}
</script>
<style scoped>
    .form{
        width: 720px;
        color: rgb(112, 112, 112);
        font: 300 12px / 15px Poppins, "Open Sans", Arial, sans-serif; 
    }

    .form-group{
        display: flex;
        justify-content: center;
        padding: 0.1rem 0;
    }
</style>
