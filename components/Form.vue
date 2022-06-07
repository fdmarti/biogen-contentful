<template>
    <div class="mt-10" v-if="showForm">
        <Input :dataInput="formFields.firstName" v-model="contentForm.firstName.value" :error="contentForm.firstName.error" @eraseError="eraseError"/>
        <Input :dataInput="formFields.lastName" v-model="contentForm.lastName.value" :error="contentForm.lastName.error" @eraseError="eraseError"/>
        <Dropdown :dataDropdown="formFields.country" v-model="contentForm.country.value" :error="contentForm.country.error" @eraseError="eraseError"/>
        <Input :dataInput="formFields.professionalId" v-model="contentForm.professionalId.value"/>
        <Input :dataInput="formFields.emailAddress" v-model="contentForm.emailAddress.value" :error="contentForm.emailAddress.error" @eraseError="eraseError"/>
        <Input :dataInput="formFields.phoneNumber" v-model="contentForm.phoneNumber.value"/>
        <Dropdown :dataDropdown="formFields.speciality" v-model="contentForm.speciality.value"/>
        <Input :dataInput="formFields.institution" v-model="contentForm.institution.value"/>
        <Richtext :dataRichtext="formFields.termsAndConditions"/>
        <Checkbox :dataCheckbox="formFields.agreeInformation" v-model="contentForm.agreeInformation.value" :error="contentForm.agreeInformation.error" @eraseError="eraseError"/>
        <Button @submitForm="submitForm"/>
    </div>

</template>
<script>
import {  createClient } from '@/plugins/contentful'
const client = createClient();

export default {
    props: ["form"],
    data() {
        return {
            iIdForm: this.form.sys.id,
            showForm : false,
            formFields: {},
            contentForm:{
                firstName: { value: '', error : false },
                lastName: { value: '', error : false },
                country: { value: null, error : false },
                professionalId: { value : ''},
                emailAddress: { value: '', error : false },
                phoneNumber: { value : ''},
                speciality: { value : null},
                institution: { value : ''},
                agreeInformation: { value : '', error : false},
            }
        };
    },

    mounted() {
        this.getFormFields()
    },

    methods: {
        async getFormFields() {
            await client.getEntry(this.iIdForm)
                .then(response => {
                this.formFields = response.fields;
                this.showForm = true;
            });
        },

        submitForm(){

            !this.contentForm.firstName.value ? this.contentForm.firstName.error = true : this.contentForm.firstName.error = false
            !this.contentForm.lastName.value ? this.contentForm.lastName.error = true : this.contentForm.lastName.error = false
            !this.contentForm.country.value ? this.contentForm.country.error = true : this.contentForm.country.error = false
            !this.contentForm.emailAddress.value ? this.contentForm.emailAddress.error = true : this.contentForm.emailAddress.error = false
            !this.contentForm.agreeInformation.value ? this.contentForm.agreeInformation.error = true : this.contentForm.agreeInformation.error = false

            const objectForm = Object.values(this.contentForm)
            let errors = 0;

            objectForm.forEach( el => {
                if (el.error) errors = errors+1
            })

            if ( !errors ) alert("Thank you for your interest in Biogen. We will be in contact with you shortly.")

            
         
        },
        eraseError(data){
            switch(data.field){
                case 'First Name*': this.contentForm.firstName.error = data.stateError; break;
                case 'Last Name*': this.contentForm.lastName.error = data.stateError; break;
                case 'Country*': this.contentForm.country.error = data.stateError; break;
                case 'Email Address*': this.contentForm.emailAddress.error = data.stateError; break;
                case 'Agree-Terms': this.contentForm.agreeInformation.error = data.stateError; break;
            }
        }
    }
}
</script>