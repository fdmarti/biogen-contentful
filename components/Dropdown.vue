<template>
    <div class="form-group">
        <div class="form">
            <div class="input">
                <label for="country">{{dropdownTitle}}</label>
                <select class="form-control" @input="$emit('input', $event.target.value)" :value="value" @change="$emit('eraseError',dropdownTitle)">
                    <option :value="value" v-for="(value, index) in dropdownData" :key="value" :disabled="index === 0" :selected="index === 0" required>{{value}}</option>
                </select>
            </div>

            <span v-if="error">
                <h4 class="errorMessage">{{dropdownError}}</h4>
            </span>

        </div>
    </div>
</template>

<script>
    import {  createClient } from '@/plugins/contentful'
    const client = createClient();

    export default {
        name: "dropdownComponent",
        props: ['dataDropdown','value','error'],
        data() {
            return {
                dropdownTitle : [],
                dropdownData : [],
                dropdownError : null
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
                        this.dropdownError = entry.fields.errorMessage
                    });
            },
        },
    }
</script>

<style scoped>
.input{
    position: relative;
}
    .input::before{
        content: '';
        position: absolute;
        left: 100%;
        top: 34px;
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
        box-shadow:none;
    }
    select:focus{
        outline: 0px;
        box-shadow: #007bff40 0px 0px 0px 0.2rem;
        border: #80bdff solid 1px;
            
    }
    option:disabled {
    color: -internal-light-dark(gretext, rgb(170, 170, 170));
}

</style>
