<script lang="ts" setup>
import { useVuelidate } from "@vuelidate/core";
import { required, email, minLength, sameAs } from "@vuelidate/validators";
import { reactive, computed } from "vue";

const state = reactive({
  email: "",
  password: {
    pass: "",
    confirm: "",
  },
});

const rules = computed(() => {
  return {
    email: { required, email },
    password: {
      pass: { required, minLength: minLength(6) },
      confirm: { required, sameAs: sameAs(state.password.pass) },
    },
  };
});

// const rules = {
//   email: { required, email },
//   password: {
//     pass: { required, minLength: minLength(6) },
//     confirm: { required, sameAs: sameAs(state.password.pass) },
//   },
// };

const v$ = useVuelidate(rules, state);

const submitForm = () => {
  // vuelidate validation
  v$.value.$validate();

  // if success
  if (!v$.value.$error) {
    alert("Form Successfully Submitted!");
  }
  // // if fail
  // else {
  //   alert(
  //     "I'm sorry, you seem to not have filled all inputs. Please fill them up and try again."
  //   );
  // }
};
</script>

<template>
  <div class="root">
    <h2>Create an Account</h2>
    <p>
      <input type="text" v-model="state.email" placeholder="Email" />
      <span v-if="v$.email.$error">
        {{ v$.email.$errors[0].$message }}
      </span>
    </p>
    <p>
      <input
        type="password"
        v-model="state.password.pass"
        placeholder="Password"
      />
      <span v-if="v$.password.pass.$error">
        {{ v$.password.pass.$errors[0].$message }}
      </span>
    </p>
    <p>
      <input
        type="password"
        v-model="state.password.confirm"
        placeholder="Confirm Password"
      />
      <span v-if="v$.password.confirm.$error">
        {{ v$.password.confirm.$errors[0].$message }}
      </span>
    </p>
    <button @click="submitForm">Submit</button>
  </div>
</template>
