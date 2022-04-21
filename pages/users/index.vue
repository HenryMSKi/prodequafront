<template>
  <div>
    <h1>Index Users</h1>
    <div class="min-h-full justify-center py-12 px-2 sm:px-6 lg:px-8">
      <div
        class="
          relative
          sm:px-10 sm:py-8
          overflow-x-auto
          shadow-md
          sm:rounded-lg
          bg-slate-50
        "
      >
        <div class="p-4">
          <label for="table-search" class="sr-only">Search</label>
          <div class="relative mt-1">
            <div
              class="
                absolute
                inset-y-0
                left-0
                flex
                items-center
                pl-3
                pointer-events-none
              "
            >
              <svg
                class="w-5 h-5 text-gray-500 dark:text-gray-400"
                fill="currentColor"
                viewBox="0 0 20 20"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  fill-rule="evenodd"
                  d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                  clip-rule="evenodd"
                ></path>
              </svg>
            </div>
            <input
              type="text"
              id="table-search"
              class="
                bg-gray-50
                border border-gray-300
                text-gray-900 text-sm
                rounded-lg
                focus:ring-blue-500 focus:border-blue-500
                block
                w-80
                pl-10
                p-2.5
                dark:bg-gray-700
                dark:border-gray-600
                dark:placeholder-gray-400
                dark:text-white
                dark:focus:ring-blue-500
                dark:focus:border-blue-500
              "
              placeholder="Search for items"
            />
          </div>
        </div>
        <table
          class="w-full text-sm text-left text-gray-500 dark:text-gray-400"
        >
          <thead
            class="
              text-xs text-black
              uppercase
              bg-gray-50
              dark:bg-slate-50 dark:text-black
              border-slate-400
            "
          >
            <tr>
              <th scope="col" class="p-4">
                <div class="flex items-center">
                  <input
                    id="checkbox-all-search"
                    type="checkbox"
                    class="
                      w-4
                      h-4
                      text-blue-600
                      bg-gray-100
                      rounded
                      focus:ring-blue-500
                      dark:focus:ring-blue-600 dark:ring-offset-gray-800
                      focus:ring-2
                      dark:bg-gray-700 dark:border-slate-400
                    "
                  />
                  <label for="checkbox-all-search" class="sr-only"
                    >checkbox</label
                  >
                </div>
              </th>
              <th scope="col" class="px-6 py-3">Product name</th>
              <th scope="col" class="px-6 py-3">Color</th>
              <th scope="col" class="px-6 py-3">Category</th>
              <th scope="col" class="px-6 py-3">Price</th>
              <th scope="col" class="px-6 py-3">
                <span class="sr-only">Edit</span>
              </th>
            </tr>
          </thead>
          <tbody v-for="user in users" :key="user.id">
            <tr
              class="bg-white text-black hover:bg-indigo-700 hover:text-white"
            >
              <td class="w-4 p-4">
                <div class="flex items-center">
                  <input
                    id="checkbox-table-search-1"
                    type="checkbox"
                    class="
                      w-4
                      h-4
                      text-blue-600
                      bg-gray-100
                      border-gray-300
                      rounded
                      focus:ring-blue-500
                      dark:focus:ring-blue-600 dark:ring-offset-gray-800
                      focus:ring-2
                      dark:bg-gray-700 dark:border-gray-600
                    "
                  />
                  <label for="checkbox-table-search-1" class="sr-only"
                    >checkbox</label
                  >
                </div>
              </td>
              <td class="px-6 py-4 font-medium">
                {{ user.id }}
              </td>
              <td scope="row" class="font-medium whitespace-nowrap px-6 py-4">
                {{ user.name }}
              </td>
              <td scope="row" class="font-medium whitespace-nowrap px-6 py-4">
                {{ user.name }}
              </td>
              <td scope="row" class="font-medium whitespace-nowrap px-6 py-4">
                {{ user.name }}
              </td>
              <td class="px-6 py-4 text-right">
                <a
                  href="#"
                  class="
                    font-medium
                    hover:underline
                    text-indigo-700
                    hover:text-white
                  "
                  ><nuxt-link :to="'users/' + user.id"> Editar </nuxt-link></a
                >
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [
        {
          id: "1",
          name: "Luis",
        },
      ],
    };
  },
  async asyncData({ $axios }) {
    try {
      const token = localStorage.getItem('t_us_con')
      this.$axios.setHeader('Authorization', 'Bearer '+token)
      const response = await $axios.$get("http://apiprodequa.mskdevmusic.com/");
      console.log(response);
      /* return { ip }; */
    } catch (error) {
      console.log(error.response);
    }
  },
};
</script>

<style>
</style>