<template>
<section :style="{ 'background-image': `url(${banner.fields.bannerImage.fields.file.url})` }" class="bg-right">
    <section class="relative h-80 flex">
        <h2 class="lg:text-4xl md:text-3xl max-w-2xl font-medium my-auto mx-auto text-white">{{banner.fields.title}}</h2>
    </section>
</section>

</template>
<script>
export default{
    props:['banner'],
}
</script>