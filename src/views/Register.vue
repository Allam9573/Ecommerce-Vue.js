<template>
  <BasicLayout>
    <div class="container">
      <div class="row text-center py-5 my-5">
        <div class="col-6 py-5">
          <h1 class="my-5">Registra una cuenta, es gratis!</h1>
          <img src="../assets/image-register.png" alt="" />
        </div>
        <div class="col-6">
          <div class="card" style="width: 30rem">
            <div class="card-header">
              <h3 class="py-3">Registro de Usuario</h3>
            </div>
            <div class="card-body">
              <form action="" @submit.prevent="register">
                <div class="form-group my-2">
                  <input
                    type="text"
                    class="form-control"
                    placeholder="Nombre de Usuario"
                    v-model="formData.username"
                  />
                </div>
                <div class="form-group my-2">
                  <input
                    type="email"
                    class="form-control"
                    placeholder="Correo Electronico"
                    v-model="formData.email"
                  />
                </div>
                <div class="form-group my-2">
                  <input
                    type="password"
                    class="form-control"
                    placeholder="Contrasenia"
                    v-model="formData.password"
                  />
                </div>
                <button type="submit" class="btn btn-primary my-2">
                  Crear Cuenta
                </button>
              </form>
              <router-link to="/login">Ya tengo una cuenta!</router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </BasicLayout>
</template>

<script>
import { ref } from "vue";
import * as Yup from "yup";
import BasicLayout from "../layout/BasicLayout.vue";
import { registerApi } from "../api/user.js";
export default {
  name: "Register",
  components: {
    BasicLayout,
  },
  setup() {
    let formData = ref({});
    let formError = ref({});
    const schemaForm = Yup.object().shape({
      username: Yup.string().required(true),
      email: Yup.string().email(true).required(true),
      password: Yup.string().required(true),
    });
    const register = async () => {
      formError.value = {};
      try {
        await schemaForm.validate(formData.value, { abortEarly: false });
        try {
          const response = await registerApi(formData.value);
          console.log(response);
        } catch (error) {
          console.log(error);
        }
      } catch (error) {
        error.inner.forEach((err) => {
          formError.value[err.path] = err.message;
        });
      }
    };
    return {
      formData,
      register,
      formError,
    };
  },
};
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>