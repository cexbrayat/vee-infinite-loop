<template>
  <div class="row">
    <div class="col-md-6 offset-md-3">
      <h1>Sign up</h1>
      <form @submit.prevent="register()">
      {{ loginField.meta }}
        <div class="form-group">
          <label for="login">Login</label>
          <input
            id="login"
            name="login"
            class="form-control"
            v-model="loginField.value"
          />
          <div v-if="loginField.meta.touched && !loginField.meta.valid" class="invalid-feedback d-block">The login is required.</div>
        </div>
        <button class="btn btn-primary" type="submit" :disabled="!formMeta.valid">Let's Go!</button>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive } from 'vue';
import { useField, useForm, defineRule } from 'vee-validate';
import { required } from '@vee-validate/rules'

defineRule('required', required);

export default defineComponent({
  name: 'Register',

  setup() {
    const { form, meta } = useForm();
    const loginField = reactive(useField('login', { required: true }, { form }));
    async function register() {
    }
    return { loginField, register, formMeta: reactive(meta) };
  }
});
</script>
