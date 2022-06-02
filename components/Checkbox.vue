<template>
  <div v-if="dataCheckbox" class="form-group">
    <section class="form">
      <input type="checkbox" class="" :id="dataCheckbox.fields.title">
      <label :for="dataCheckbox.fields.title">{{dataCheckbox.fields.checkbox.join()}}*</label>
    </section>
  </div>
</template>

<script>
export default {
    props : ['dataCheckbox']
}
</script>

<style scoped>

    .form-group{
        margin-top: 10px;
        display: flex;
        justify-content: center;
        align-content: center;
        padding: 0.1rem 0;
    }

    .form{
        width: 720px;
        color: rgb(112, 112, 112);
        font: 300 12px / 15px Poppins, "Open Sans", Arial, sans-serif; 
    }

    input{
        position: relative;
        z-index: 1;
        max-width: 19px;
        height: 19px;
        margin: 0px 12px 0px 0px;
        cursor: pointer;
    }
    input::before{
        content: "";
        position: absolute;
        z-index: 1;
        top: 1px;
        left: 1px;
        width: 17px;
        height: 17px;
        outline: rgb(204, 204, 204) solid 1px;
        border: 3px solid rgb(255, 255, 255);
        pointer-events: all;
    }
</style>