<template>
<section class="flex justify-start py-9">
    <img :src="header.fields.headerLogo.fields.file.url" alt="logo biogen">
</section>

</template>
<script>
export default{
    props:['header']
}
</script>