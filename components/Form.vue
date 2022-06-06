<template>
    <div class="mt-10" v-if="showForm">
        <Input :dataInput="formFields.firstName" v-model="contentForm.firstName.value" :error="contentForm.firstName.error"/>
        <Input :dataInput="formFields.lastName" v-model="contentForm.lastName.value" :error="contentForm.lastName.error"/>
        <Dropdown :dataDropdown="formFields.country" v-model="contentForm.country.value" :error="contentForm.country.error"/>
        <Input :dataInput="formFields.professionalId" v-model="contentForm.professionalId.value"/>
        <Input :dataInput="formFields.emailAddress" v-model="contentForm.emailAddress.value" :error="contentForm.emailAddress.error"/>
        <Input :dataInput="formFields.phoneNumber" v-model="contentForm.phoneNumber.value"/>
        <Dropdown :dataDropdown="formFields.speciality" v-model="contentForm.speciality.value"/>
        <Input :dataInput="formFields.institution" v-model="contentForm.institution.value"/>
        <Richtext :dataRichtext="formFields.termsAndConditions"/>
        <Checkbox :dataCheckbox="formFields.agreeInformation" v-model="contentForm.agreeInformation.value" :error="contentForm.agreeInformation.error"/>
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
                agreeInformation: { value : false},
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

            if ( !errors ) console.log("aca se mandaria el form")

            
         
        }
    }
}
</script>