<template>
  <div>
    <header class="sticky top-0">
      <div class="bg-indigo-600 relative items-center">
        <nav class="flex items-center justify-between flex-wrap p-6">
          <div class="flex items-center flex-shrink-0 text-white mr-6">
            <button
              class="
                inline-flex
                items-center
                justify-center
                p-2
                rounded-md
                text-white
                hover:text-white hover:bg-indigo-500
                focus:outline-none
                focus:ring-2
                focus:ring-inset
                focus:ring-white
              "
              @click="clickRegistrarUsuarios()"
            >
            Registrar usuario 
            </button>
            &nbsp;

            <button
              class="
                inline-flex
                items-center
                justify-center
                p-2
                rounded-md
                text-white
                hover:text-white hover:bg-indigo-500
                focus:outline-none
                focus:ring-2
                focus:ring-inset
                focus:ring-white
              "
              @click="clickListarUsuario()"
            >
               Lista de usuarios
            </button>
            &nbsp;

            &nbsp;
          </div>
          <div class="flex items-center flex-shrink-0 text-white mr-6">
            <button
              @click="clickCerrarSesion()"
              class="
                inline-flex
                items-center
                justify-center
                p-2
                rounded-md
                text-white
                hover:text-white hover:bg-indigo-500
                focus:outline-none
                focus:ring-2
                focus:ring-inset
                focus:ring-white
              "
            >
              Cerrar Sesion
            </button>
          </div>
        </nav>
      </div>
    </header>
    <Nuxt />
    <footer class="fixed inset-x-0 bottom-0 ">&copy; {{new Date().getFullYear()}}</footer>
  </div>
</template>

<script>
export default {
  methods: {
    clickCerrarSesion() {
      localStorage.removeItem("t_us_con")
      this.$router.push("/");
    },
    clickRegistrarUsuarios(){
      this.$router.push("/users/register")
    },
    clickListarUsuario(){
      this.$router.push("/users")
    }
  },
};
</script>

<style>
</style>