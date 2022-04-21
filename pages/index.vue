<template>
  <div>
    <div
      class="
        min-h-full
        flex
        items-center
        justify-center
        py-12
        px-4
        sm:px-6
        lg:px-8
      "
    >
      <div class="max-w-md w-full space-y-8">
        <div>
          <img
            class="mx-auto h-12 w-auto"
            src="https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg"
            alt="Workflow"
          />
          <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-900">
            Iniciar Sesión
          </h2>
        </div>
        <input type="hidden" name="remember" value="true" />
        <div class="rounded-md shadow-sm -space-y-px">
          <div>
            <label for="email-address" class="sr-only">Email address</label>
            <input
              id="email-address"
              name="email"
              type="email"
              autocomplete="email"
              required=""
              class="
                appearance-none
                rounded-none
                relative
                block
                w-full
                px-3
                py-2
                border border-gray-300
                placeholder-gray-500
                text-gray-900
                rounded-t-md
                focus:outline-none
                focus:ring-indigo-500
                focus:border-indigo-500
                focus:z-10
                sm:text-sm
              "
              placeholder="Email address"
              v-model="user.correoUsuario"
            />
          </div>
          <div>
            <label for="password" class="sr-only">Password</label>
            <input
              id="password"
              name="password"
              type="password"
              autocomplete="current-password"
              required=""
              class="
                appearance-none
                rounded-none
                relative
                block
                w-full
                px-3
                py-2
                border border-gray-300
                placeholder-gray-500
                text-gray-900
                rounded-b-md
                focus:outline-none
                focus:ring-indigo-500
                focus:border-indigo-500
                focus:z-10
                sm:text-sm
              "
              placeholder="Password"
              v-model="user.passwordUsuario"
            />
          </div>
        </div>

        <div class="flex items-center justify-between">
          <div class="text-sm">
            <a
              href="#"
              class="font-medium text-indigo-600 hover:text-indigo-500"
            >
              Forgot your password?
            </a>
          </div>
        </div>

        <div>
          <button
            @click="iniciarSesión(user)"
            class="
              group
              relative
              w-full
              flex
              justify-center
              py-2
              px-4
              border border-transparent
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
          >
            <span
              class="
                absolute
                left-0
                inset-y-0
                flex
                items-center
                pl-3
                material-icons
              "
            >
              lock
            </span>
            Iniciar Sesión
          </button>
        </div>
      </div>
    </div>
    <!-- {{
      $nuxt.$route.path ? 'Inicio' : "Principal"
      }} -->
    <!-- {{user}} -->
  </div>
</template>

<script>
export default {
  methods: {
    async iniciarSesión(user) {
      console.log(user);
      try {
        const resp = await this.$axios.$post("https://prodequaapi.herokuapp.com/auth", {
          correoUsuario: user.correoUsuario,
          passwordUsuario: user.passwordUsuario,
        });

        localStorage.setItem("t_us_con", resp.token);
        console.log(resp);
        this.$router.push("/users");
      } catch (error) {
        console.log(error.response.data.message);
      }
    },
  },
  name: "IndexPage",
  layout: "auth",
  data() {
    return {
      user: [],
    };
  },
};
</script>

<style>
</style>
