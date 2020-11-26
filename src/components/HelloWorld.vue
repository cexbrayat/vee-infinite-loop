<template>
  <h1>Register</h1>
  <Form>
    <Field as="input" rules="required" name="login" :label="label" />
    <ErrorMessage name="login" as="div"/>
    <button @click="label = 'other'">Change label</button>
  </Form>

</template>

<script>
import { ref } from 'vue';
import { defineRule, ErrorMessage, Form, Field } from 'vee-validate'
import { required } from '@vee-validate/rules'

defineRule('required', required);

export default {
  components: {
    Form,
    Field,
    ErrorMessage
  },
  setup() {
    const label = ref('login');
    return {
      label
    }
  }
}
</script>
