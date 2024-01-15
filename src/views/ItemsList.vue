<template>
  <HeaderWrapper>
    
    <div class="mx-5 px-5">
      <h3 class="text-grey-700">Completed Records Filter</h3><br>
      <label class="flex cursor-pointer select-none items-center">
        <div class="animate-bounce relative">
          <input type="checkbox" class="sr-only" @change="handleCheckboxChange" />
          <div class="block h-8 w-14 rounded-full bg-[#E5E7EB]"></div>
          <div
            :class="{ 'translate-x-full bg-active': isChecked }"
            class="dot absolute left-1 top-1 h-6 w-6 rounded-full bg-white transition"
          ></div>
          
        </div>
      </label>
      <div class="flex flex-col">
        <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div class="inline-block min-w-full py-2 sm:px-6 lg:px-8">
            <div class="relative overflow-x-auto">
              <table class="mt-8 w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                <thead
                  class="text-xs text-gray-700 uppercase bg-blue-50 dark:bg-gray-700 dark:text-gray-400"
                >
                  <tr>
                    <th scope="col" class="px-6 py-4">#</th>
                    <th scope="col" class="px-6 py-4">User Id</th>
                    <th scope="col" class="px-6 py-4">Title</th>
                    <th scope="col" class="px-6 py-4">Completed</th>
                    <th scope="col" class="px-6 py-4">Actions</th>
                  </tr>
                </thead>
                <tbody v-if="isLoaded">
                 
                  <tr v-bind:class="{
                    'border-b  dark:border-neutral-500 dark:bg-neutral-700': true,
                    'bg-green-200 dark:bg-green-700': item.completed
                  }"
                    class="border-b  dark:border-neutral-500 dark:bg-neutral-700"
                    v-for="(item, index) in items"
                    :key="index">
                  
                    <td class="whitespace-nowrap px-6 py-4 font-medium">{{ index + 1 }}</td>
                    <td class="whitespace-nowrap px-6 py-4">{{ item.userId }}</td>
                    <td class="whitespace-nowrap px-6 py-4">{{ item.title }}</td>
                    <td class="whitespace-nowrap px-6 py-4">{{ item.completed ? 'Yes' : 'No' }}</td>
                    <td>
                      <input type="checkbox" id="checkbox" v-model="item.completed" />
                    </td>
                  
                  </tr>
               
                </tbody>
              </table>
              <div
                v-if="!isLoaded"
                class="loader inline-block h-8 w-8 animate-spin rounded-full border-4 border-solid border-current border-r-transparent align-[-0.125em] motion-reduce:animate-[spin_1.5s_linear_infinite]"
                role="status"
              >
                <span
                  class="!absolute !-m-px !h-px !w-px !overflow-hidden !whitespace-nowrap !border-0 !p-0 ![clip:rect(0,0,0,0)]"
                  >Loading...</span
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </HeaderWrapper>
</template>

<script>
import HeaderWrapper from '../components/HeaderWrapper.vue'
export default {
  data() {
    return {
      isChecked: false,
      isLoaded: false
    }
  },
  mounted() {
    this.$store
      .dispatch('fetchItems')
      .then(() => {
        this.isLoaded = true
      })
      .catch(() => {
        this.isLoaded = true
      })
  },
  components: {
    HeaderWrapper
  },
  methods: {
    changeStatus(status)
    {
      console.log('status...', status)
    },
    handleCheckboxChange() {
      this.isChecked = !this.isChecked
    }
  },
  computed: {
    items() {
      let items = this.$store.state.items
      if (this.isChecked) {
        return items.filter((i) => i.completed == true)
      }
      return items
    }
  }
}
</script>
<style>
  .v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
