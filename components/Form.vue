<template>
    <div class="mt-10">
        <Input :dataInput="formFields.firstName"/>
        <Input :dataInput="formFields.lastName"/>
        <Dropdown/>
        <Input :dataInput="formFields.professionalId"/>
        <Input :dataInput="formFields.phoneNumber"/>
        <Dropdown/>
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
            formFields: {},
        };
    },
    mounted() {
        this.getFormFields();
    },
    methods: {
        getFormFields() {
            client.getEntry(this.iIdForm)
                .then(response => {
                this.formFields = response.fields;
            });
        }
    }
}
</script>