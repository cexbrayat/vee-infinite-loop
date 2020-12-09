<template>
  <h1>Register</h1>
  <Form :initialValues="{ max: 5 }">
    <div>
      <label for="number1">Number less than 3</label>
      <Field name="number1" rules="lessThan:3" v-slot="{ field }">
        <input id="number1" type="number" v-bind="field">
      </Field>
      <div>
        <ErrorMessage name="number1" />
      </div>
    </div>

    <div>
      <label for="max">Max</label>
      <Field name="max" v-slot="{ field }">
        <input id="max" type="number" v-bind="field">
      </Field>
    </div>
    <div>
      <label for="number2">Number less than max field</label>
      <Field name="number2" rules="lessThan:@max" v-slot="{ field }">
        <input id="number2" type="number" v-bind="field">
      </Field>
      <div>
        <ErrorMessage name="number2" />
      </div>
    </div>
  </Form>

</template>

<script>
import { defineRule, ErrorMessage, Form, Field, configure } from 'vee-validate'

defineRule('lessThan', (value, params) => Number(value) < Number(params[0]))
configure({
  validateOnInput: true,
  generateMessage: (context) => {
    const params = context.rule.params;
    return `This value must be less than ${params[0]}`;
  }
});

export default {
  components: {
    Form,
    Field,
    ErrorMessage
  }
}
</script>
