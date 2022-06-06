<template>
    <div class="form-group">
        <section class="form">
            <button @click="$emit('submitForm')">Submit</button>
        </section>
    </div>
</template>

<script>
export default {

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
    button{
        background-color: #8bbd35;
        border-color: #88b933;
        align-items: center;
        width: 168px;
        min-height: 46px;
        border-radius: 0.25rem;
        color: rgb(255, 255, 255);
        font: 20px / 24px Poppins, "Open Sans", Arial, sans-serif;
        cursor: pointer;
        margin:38px 0px 0px;
    }

    button:hover{
        transform: translateY(-1px);
        box-shadow: rgb(0 0 0 / 20%) 0px 5px 10px;
    }

    button:focus{
        box-shadow: rgb(116 157 44) 0px 0px 0px 0.2rem;
        outline: none;
    }
</style>