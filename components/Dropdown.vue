<template>
    <div class="form-group">
        <div class="form">
            <div class="input">
                <label for="country">{{dropdownTitle}}</label>
                <select class="form-control">
                    <option :value="value" v-for="(value, index) in dropdownData" :key="value" :disabled="index === 0" :selected="index === 0" required>{{value}}</option>
                </select>
                <div class="arrow"></div>
            </div>

        </div>
    </div>
</template>

<script>
    import {  createClient } from '@/plugins/contentful'
    const client = createClient();

    export default {
        name: "dropdownComponent",
        props: ['dataDropdown'],
        data() {
            return {
                dropdownTitle : [],
                dropdownData : []
            };
        },
        mounted(){
            this.getCountries(this.dataDropdown.sys.id);
        },
 
        methods: {
            async getCountries(iIdEntry) {
                await client.getEntry(iIdEntry)
                    .then(entry => {
                        this.dropdownTitle  = entry.fields.title
                        this.dropdownData = entry.fields.label
                    });
            },
        },
    }
</script>

<style scoped>
    .form{
        width: 720px;
    }
    .form-group{
        display: flex;
        justify-content: center;
        margin: -30px 0 10px 0;
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
    .input::before{
        content: '';
        position: relative;
        left: 100%;
        top: 61px;
        width: 0; 
        height: 0; 
        border-left: 5px solid transparent;
        border-right: 5px solid transparent;
        border-top: 5px solid #707070;
        margin-left: -21px;
    }
    select{
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
