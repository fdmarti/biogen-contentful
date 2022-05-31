<template>
  <div class="bg-gray-300 p-10 m-5 rounded-md">
    <section>
      <h2 class="text-2xl mb-2">{{blog.title}}</h2>
      <p>{{blog.content}}</p>
    </section>
    <img v-for="(image,index) in blog.image" :key="index" :src="image.fields.file.url" :alt="image.fields.file.title" class="h-30 w-40 mt-5">
    <section class="mt-5">
      <Categories :categories="blog.categories"/>
    </section>
  </div>
</template>
<script>
export default{
    props: ["blog"],
}

</script>