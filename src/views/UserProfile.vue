<template>
  <HeaderWrapper>
    <div class="flex items-center h-screen w-full justify-center">
      <div class="max-w-xs">
        <div class="bg-white shadow-xl rounded-lg py-3">
          <div class="photo-wrapper p-2">
            <img
              class="w-32 h-32 rounded-full mx-auto"
              src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/4aa68f80-158e-4744-95e9-da53a23e1eba/dasli0e-0189993a-d23c-4825-a6fc-aa0403374080.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcLzRhYTY4ZjgwLTE1OGUtNDc0NC05NWU5LWRhNTNhMjNlMWViYVwvZGFzbGkwZS0wMTg5OTkzYS1kMjNjLTQ4MjUtYTZmYy1hYTA0MDMzNzQwODAucG5nIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.fIqn95jSk9V2Ue2AWhx7Ow8k4B1T7to-RjMXJs04mmA"
              alt="John Doe"
            />
          </div>
          <div class="p-2">
            <h3 class="text-center text-xl text-gray-900 font-medium leading-8">{{ user.name }}</h3>
            <div class="text-center text-gray-400 text-xs font-semibold">
              <p>{{user.designation}}</p>
            </div>
            <table class="text-xs my-3">
              <tbody>
                <tr>
                  <td class="px-2 py-2 text-gray-500 font-semibold">Address</td>
                  <td class="px-2 py-2">{{ user.address }}</td>
                </tr>
                <tr>
                  <td class="px-2 py-2 text-gray-500 font-semibold">Phone</td>
                  <td class="px-2 py-2">{{ user.phone }}</td>
                </tr>
                <tr>
                  <td class="px-2 py-2 text-gray-500 font-semibold">Email</td>
                  <td class="px-2 py-2">{{ user.email }}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </HeaderWrapper>
</template>

<script>
import HeaderWrapper from '../components/HeaderWrapper.vue'
export default {
  components: {
    HeaderWrapper
  },
  computed: {
    user(){
        return this.$store.state.authUser
    }
  }
}
</script>
