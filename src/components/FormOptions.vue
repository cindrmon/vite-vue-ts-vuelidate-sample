<script lang="ts">
import useVuelidate from "@vuelidate/core";
import { required } from "@vuelidate/validators";

export default {
  data() {
    return {
      v$: useVuelidate(),
      email: "",
      password: {
        pass: "",
        confirm: "",
      },
    };
  },
  validations() {
    return {
      email: { required },
      password: {
        pass: { required },
        confirm: { required },
      },
    };
  },
  methods: {
    submitForm() {
      // vuelidate validation
      this.v$.$validate();

      // if success
      if (!this.v$.$error) {
        alert("Form Successfully Submitted!");
      }
      // if fail
      else {
        alert(
          "I'm sorry, you seem to not have filled all inputs. Please fill them up and try again."
        );
      }
    },
  },
};
</script>

<template>
  <div class="root">
    <h2>Create an Account</h2>
    <p>
      <input type="text" v-model="email" placeholder="Email" />
    </p>
    <p>
      <input type="password" v-model="password.pass" placeholder="Password" />
    </p>
    <p>
      <input
        type="password"
        v-model="password.confirm"
        placeholder="Confirm Password"
      />
    </p>
    <button @click="submitForm">Submit</button>
  </div>
</template>
