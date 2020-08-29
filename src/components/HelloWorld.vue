<template>
  <h1>Register</h1>
  <Form @submit="register($event)" v-slot="{ meta: formMeta }">
     <Field name="login" rules="required" v-slot="{ field }" v-model="user.name">
      <label for="login">Login</label>
      <input id="login" v-bind="field" />
      <ErrorMessage name="login" />
    </Field>
    <button :disabled="formMeta.invalid">Register</button>
  </Form>

</template>

<script>
import { reactive } from 'vue'
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
    const user = reactive({ name: '' });
      function register(values) {
      console.log(values); // or console.log(user)
    }
    return { user, register };
  }
}
</script>
