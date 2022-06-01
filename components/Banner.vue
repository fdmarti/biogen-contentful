<template>
<section :class="`bg-[url(${banner.fields.bannerImage.fields.file.url})]`">
    <img class="absolute bg-center" :src="banner.fields.bannerImage.fields.file.url" alt="banner image">
    <section class="relative h-80 flex">
        <h2 class="text-4xl max-w-2xl font-medium my-auto mx-auto text-white">{{banner.fields.title}}</h2>
    </section>
</section>

</template>
<script>
export default{
    props:['banner'],
}
</script>