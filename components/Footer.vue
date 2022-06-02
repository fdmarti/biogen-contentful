<template>
    <div class="footer-group">
        <section class="footer">
        <p>
            <a href="https://cp-author.biogen-support.com/content/intl/eu/eu/mta/hcp/landing-pages/master-templates/en/cookies.html">
            {{footer.fields.externalLink}}</a>
        </p>

        <div>
            <a href="https://www.biogen.com/">
                <img :src="footer.fields.footerImage.fields.file.url" :alt="footer.fields.footerImage.fields.file.description"><br>
            </a>
            <div>
                <span v-for="(content,indexContent) in footer.fields.footerData.content" :key="indexContent">
                    <p v-for="(field,indexField) in content.content" :key="indexField" class="text-footer">
                        {{field.value}}                   
                    </p>
                </span>
            </div>
        </div>
        </section>
    </div>
</template>

<script>
export default {
    props:['footer']
}
</script>

<style scoped>
    .footer{
        width: 720px;
        display: flex;
        justify-content: space-between;
    }
    .footer-group{
        display: flex;
        justify-content: center;
        padding: 2rem 0;
    }

    a{
        color: rgb(112, 112, 112);
        text-decoration: underline;
        font: 0.875em Poppins, "Open Sans", Arial, sans-serif;
    }

    a:hover{
        text-decoration: none;
    }

    .text-footer{
        color: rgb(112, 112, 112);
        width: 150px;
        text-align: right;
        font: 11px / 130% Poppins, "Open Sans", Arial, sans-serif;
        margin-bottom: 1rem;
    }
</style>