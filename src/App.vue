<template>
  <div class="container">
    <h1>Custom validation</h1>
    <CustomValidations/>
    <h1>Form value binding</h1>
    <ValueBindingForm />
    <h1>Custom form validations</h1>
    <FormValidations />
    <h1>Basic form validations</h1>
    <BasicForm />
  </div>
</template>

<script>
import BasicForm from "./components/BasicForm.vue";
import FormValidations from "./components/FormValidations.vue";
import ValueBindingForm from "./components/ValueBindingForm.vue";
import CustomValidations from "./components/CustomValidation.vue";
export default {
  name: "app",
  components: {
    CustomValidations,
    BasicForm,
    FormValidations,
    ValueBindingForm,
  },
};
</script>
