<template>
  <Form @submit="register($event)" v-slot="{ meta: formMeta }">
    <Field name="password" rules="required|min:3" v-slot="{ field, meta }" v-model="user.password">
      <label for="password" :class="{ 'text-danger': meta.failed }">Password</label>
      <input id="password" type="password" :class="{ 'is-invalid': meta.failed }" v-bind="field" />
      <ErrorMessage name="password" class="error" />
    </Field>
    <Field
      name="confirmPassword"
      rules="required|confirmed:@password"
      label="password confirmation"
      v-slot="{ field, meta }"
      v-model="user.confirmPassword"
    >
      <label for="confirm-password" :class="{ 'text-danger': meta.failed }">Confirm password</label>
      <input id="confirm-password" type="password" :class="{ 'is-invalid': meta.failed }" v-bind="field" />
      <ErrorMessage name="confirmPassword" class="error" />
    </Field>
    <button :disabled="formMeta.invalid">Register</button>
  </Form>
  </template>

<script lang="ts">
/* eslint-disable no-console */
import { defineComponent, reactive } from 'vue';
import { defineRule, ErrorMessage, Field, Form } from 'vee-validate';
import { confirmed, min, required } from '@vee-validate/rules';

defineRule('min', min);
defineRule('required', required);
defineRule('confirmed', confirmed);

export default defineComponent({
  name: 'Register',
  components: {
    ErrorMessage,
    Field,
    Form
  },
  setup() {
    const user = reactive({ name: 'JB', password: '', confirmPassword: '' });

    function register(values) {
      console.log(values); // or console.log(user)
    }

    return { user, register };
  }
});
</script>
