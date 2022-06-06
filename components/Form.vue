<template>
    <div class="mt-10" v-if="showForm">
        <Input :dataInput="formFields.firstName"/>
        <Input :dataInput="formFields.lastName"/>
        <Dropdown :dataDropdown="formFields.country"/>
        <Input :dataInput="formFields.professionalId"/>
        <Input :dataInput="formFields.emailAddress"/>
        <Input :dataInput="formFields.phoneNumber"/>
        <Dropdown :dataDropdown="formFields.speciality"/>
        <Input :dataInput="formFields.institution"/>
        <Richtext :dataRichtext="formFields.termsAndConditions"/>
        <Checkbox :dataCheckbox="formFields.agreeInformation"/>
        <Button />
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
        }
    }
}
</script>