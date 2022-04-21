<template>
  <div class="min-h-full justify-center py-12 px-2 sm:px-6 lg:px-8">
    <div class="">
      <h3 class="text-lg font-medium leading-6 text-gray-900">
        Registrar nuevo usuario
      </h3>
      <p class="mt-1 text-sm text-gray-600">
        Ingresar todos los datos solicitados.
      </p>
    </div>
    <div class="shadow overflow-hidden sm:rounded-md">
      <div class="px-4 py-5 bg-white sm:p-6">
        <div class="grid grid-cols-6 gap-10">
          <div class="col-span-6 sm:col-span-3">
            <label
              for="first-name"
              class="block text-sm font-medium text-gray-700"
              >Nombre</label
            >
            <input
              type="text"
              name="first-name"
              id="first-name"
              autocomplete="given-name"
              class="
                mt-1
                focus:ring-indigo-500 focus:border-indigo-500
                block
                w-full
                shadow-sm
                sm:text-sm
                border-gray-300
                rounded-md
              "
              v-model="userPost.nombreUsuario"
            />
          </div>

          <div class="col-span-6 sm:col-span-3">
            <label
              for="last-name"
              class="block text-sm font-medium text-gray-700"
              >Apellido</label
            >
            <input
              type="text"
              name="last-name"
              id="last-name"
              autocomplete="family-name"
              class="
                mt-1
                focus:ring-indigo-500 focus:border-indigo-500
                block
                w-full
                shadow-sm
                sm:text-sm
                border-gray-300
                rounded-md
              "
              v-model="userPost.apellidoUsuario"
            />
          </div>

          <div class="col-span-6 sm:col-span-4">
            <label
              for="email-address"
              class="block text-sm font-medium text-gray-700"
              >Correo</label
            >
            <input
              type="text"
              name="email-address"
              id="email-address"
              autocomplete="email"
              class="
                mt-1
                focus:ring-indigo-500 focus:border-indigo-500
                block
                w-full
                shadow-sm
                sm:text-sm
                border-gray-300
                rounded-md
              "
              v-model="userPost.correoUsuario"
            />
          </div>

          <div class="col-span-6 sm:col-span-3">
            <label for="country" class="block text-sm font-medium text-gray-700"
              >Rol</label
            >
            <select
              id="country"
              name="country"
              autocomplete="country-name"
              class="
                mt-1
                block
                w-full
                py-2
                px-3
                border border-gray-300
                bg-white
                rounded-md
                shadow-sm
                focus:outline-none focus:ring-indigo-500 focus:border-indigo-500
                sm:text-sm
              "
              v-model="select"
            >
              <option value="1">Administrador de Sistema</option>
              <option value="2">Usuario General</option>
            </select>
          </div>

          <div class="col-span-6">
            <label
              for="street-address"
              class="block text-sm font-medium text-gray-700"
              >Clave Usuario</label
            >
            <input
              type="password"
              name="street-address"
              id="street-address"
              autocomplete="street-address"
              class="
                mt-1
                focus:ring-indigo-500 focus:border-indigo-500
                block
                w-full
                shadow-sm
                sm:text-sm
                border-gray-300
                rounded-md
              "
              v-model="userPost.passwordUsuario"
            />
          </div>

          <div class="px-4 py-3 bg-gray-50 text-right sm:px-6">
            <button
              class="
                inline-flex
                justify-center
                py-2
                px-4
                border border-transparent
                shadow-sm
                text-sm
                font-medium
                rounded-md
                text-white
                bg-indigo-600
                hover:bg-indigo-700
                focus:outline-none
                focus:ring-2
                focus:ring-offset-2
                focus:ring-indigo-500
              "
              @click="guardarUsuario(userPost, select)"
            >
              Save
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userPost: [],
      select: "",
    };
  },
  methods: {
    async guardarUsuario(userPost, select) {
      console.log(select);
      console.log(userPost);
      try {
        const token = localStorage.getItem("t_us_con");
        this.$axios.setHeader("Authorization", "Bearer " + token);
        const resp = await this.$axios.$post("http://apiprodequa.mskdevmusic.com/", {
          nombreUsuario: userPost.nombreUsuario,
          correoUsuario: userPost.correoUsuario,
          apellidoUsuario: userPost.apellidoUsuario,
          passwordUsuario: userPost.passwordUsuario,
          idRol: select,
        });
        console.log(resp);
        this.$router.push("/users");
      } catch (error) {
        console.log(error.response.data.message);
      }
    },
  },
};
</script>

<style>
</style>