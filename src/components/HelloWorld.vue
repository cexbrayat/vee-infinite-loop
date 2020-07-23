<template>
  <h1>Register</h1>
  <Form>
    <Field as="input" :rules="{ required: true }" name="login" />
    <ErrorMessage name="login" as="div"/>
  </Form>

</template>

<script>
import { defineRule, ErrorMessage, Form, Field } from 'vee-validate'
import { required } from '@vee-validate/rules'

defineRule('required', required);

export default {
  components: {
    Form,
    Field,
    ErrorMessage
  }
}
</script>
