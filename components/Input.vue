<template>
    <div class="form-group" v-if="dataInput">
        <div class="form">
            <div class="input">
                <label>{{dataInput.fields.label}}</label>
                <input 
                    :type="dataInput.fields.type" 
                    class="form-control"
                    @input="$emit('input', $event.target.value)"
                    :value="value"
                    :class="stateInput"
                    v-model="inputValue"
                    @keyup="isValidField(dataInput.fields)"
                    @blur="isValidField(dataInput.fields)"
                >
            </div>
            <span v-if="error">
                <h4 class="errorMessage">{{dataInput.fields.errorMessage}}</h4>
            </span>
            
        </div>
    </div>
</template>

<script>
    export default {
        name: "inputComponent",
        props:['dataInput','value','error'],
        data() {
            return {
                stateInput: '',
                inputValue : ''
            }
        },

        methods:{
            isValidField(fieldData){
                if ( this.error === undefined ) {
                    this.stateInput = 'valid'
                } else 
                    { 
                        let stateField = false;
                        if ( this.inputValue.length > 0 ){
                            this.stateInput = 'valid';
                            stateField = false;
                        }else{
                            this.stateInput = 'invalid' 
                            stateField = true;
                        }

                        this.$emit('eraseError',{ field : fieldData.label , stateError : stateField})
                    }
            }
        }
    }
</script>

<style>
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
    input:focus{
        outline: #007bff40 solid 3.5px;
        border: #80bdff solid 1px;
    }
    .valid{
        border: #28a745 solid 1px;
    }
    .valid:focus{
        outline: #28a74540 solid 3.5px;
        border: #28a745 solid 1px;
    }

    .invalid:focus{
        outline: #dc354540 solid 3.5px;
        border: #dc3545 solid 1px;
    }
    .invalid{
        border: #dc3545 solid 1px;
    }

    .errorMessage{
        font: 300 11px/13px Poppins, 'Open Sans', Arial, sans-serif;
        width: 100%;
        margin: -0.5rem 0 0.15rem;
        color: #dc3545;
    }


</style>
