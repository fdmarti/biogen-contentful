<template>
    <div class="form-group" v-if="dataInput">
        <div class="form">
            <div class="input">
                <label for="country">{{dataInput.fields.label}}</label>
                <input type="text" class="form-control">
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "inputComponent",
        props:['dataInput']
    }
</script>

<style scoped>
    .form{
        width: 720px;
    }
    .form-group{
        display: flex;
        justify-content: center;
        padding: 0.1rem 0;
    }
    label{
        color: rgb(112, 112, 112);
        font: 300 12px / 15px Poppins, "Open Sans", Arial, sans-serif; 
        display: block;
        margin-bottom: 5px;
    }
    .input{
        min-height: 66px;
    }

    input{
        min-width: 100%;
        color: rgb(112, 112, 112);
        font: 300 14px / 15px Poppins, "Open Sans", Arial, sans-serif; 
        background-color: rgb(255, 255, 255);
        background-clip: padding-box;
        border: 1px solid rgb(206, 212, 218);
        border-radius: 0.25rem;
        height: 32px;
        padding-left: 10px;
        appearance: none;
    }

    option:disabled {
    color: -internal-light-dark(gretext, rgb(170, 170, 170));
}

</style>
