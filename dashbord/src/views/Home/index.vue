<template>
  <custom-header
    @create-account="handleAccountCreate"
    @login="hanfleLogin"
   />
  <contact />
  <footer class="flex justify-center py-10 bg-brad-gray">
    <p class="font-medim text-center text-gray-800">feedbacker 2021</p>
  </footer>
</template>

<script>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'
import CustomHeader from './CustomHeader'
import Contact from './Contact'

export default {
  components: {
    CustomHeader,
    Contact
  },
  setup () {
    const router = useRouter()

    onMounted(() => {
      const token = window.localStorage.getItem('token')
      if (token) {
        router.push({ name: 'Feedback' })
      }
    })
    function hanfleLogin () {}
    function handleAccountCreate () {}
    return {
      hanfleLogin,
      handleAccountCreate
    }
  }
}
</script>
