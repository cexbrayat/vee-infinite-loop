<template>
  <h1>Register</h1>
  <Form>
    <Field as="input" rules="required" name="login" v-model="user.name"/>
    <ErrorMessage name="login" as="div"/>
  </Form>

</template>

<script>
import { reactive } from 'vue';
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
    const user = reactive({ name: 'ced' });
    return { user }
  }
}
</script>
