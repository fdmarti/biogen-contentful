<template>
  <div v-if="dataCheckbox" class="form-group">
    <section class="form">
      <input 
      :id="dataCheckbox.fields.title"
      type="checkbox" 
      class="form-control"
      @input="$emit('input', $event.target.value)" :value="value">
      <label :for="dataCheckbox.fields.title">{{dataCheckbox.fields.checkbox.join()}}*</label>
    </section>
    
    <span v-if="error">
      <h4 class="errorMessage">{{dataCheckbox.fields.errorMessage}}</h4>
    </span>

  </div>
</template>

<script>
export default {
    props : ['dataCheckbox', 'error'],
}
</script>

<style scoped>

    .form-group{
        margin-top: 10px;
        display: block;
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
        color: rgb(112, 112, 112);
        font: 400 14px / 15px Poppins, "Open Sans", Arial, sans-serif;
        border: solid 1px transparent;
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
        background-color: #fff;
    }
    input:checked:before{
      background:  0% 0% / 10px 10px rgb(204, 204, 204);
    }
    label, input{
      display: inline;
    }
    input:focus{
        outline: none;
        border: none;
    }

</style>