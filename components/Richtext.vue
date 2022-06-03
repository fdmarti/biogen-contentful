<template>
    <div v-if="dataRichtext" class="form-group">
        <section class="text-group">
            <RichTextRenderer :document="dataRichtext.fields.content" class="form"/>
        </section>
    </div>
</template>
<script>
import RichTextRenderer from 'contentful-rich-text-vue-renderer';

export default {
    props: ["dataRichtext"],
    components: {RichTextRenderer}
}
</script>
<style scoped>
    p{
        color: rgb(112, 112, 112);
        font: 12px / 14px Poppins, "Open Sans", Arial, sans-serif;
        margin-bottom: 2rem;
    }

    a{
        text-decoration: underline;
    }

    .form-group{
        display: flex;
        justify-content: center;
    }

    .text-group{
        width: 720px;
        justify-content: center;
    }
</style>
