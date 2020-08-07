<template>
  <form @submit.prevent="register()">
    <label for="name">Name</label>
    <input id="name" v-model="name.value" />
    <div class="error">{{ name.errorMessage }}</div>
    <button :disabled="formMeta.invalid">Register</button>
  </form>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { useField, useForm } from 'vee-validate';

export default defineComponent({
  name: 'Register',
  setup() {
    const { form, meta: formMeta, values: formValues } = useForm(/*{ initialValues: { name: 'JB' } }*/);
    // add a `name` field to the form, initialized with 'JB'
    const name = useField('name', { required: true }, { form, initialValue: 'JB' });
    function register() {
    }
    return { name, formMeta, register };
  }
});
</script>
