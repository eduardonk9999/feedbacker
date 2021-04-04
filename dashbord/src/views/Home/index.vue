<template>
  <div>
    <custom-header
      @create-account="handleAccountCreate"
      @login="handleLogin"
    />
    <contact />
    <footer class="flex justify-center py-10 bg-brad-gray">
      <p class="font-medim text-center text-gray-800">feedbacker 2021</p>
    </footer>
  </div>
</template>

<script>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'
import CustomHeader from './CustomHeader'
import Contact from './Contact'
import useModal from '../../hooks/useModal'

export default {
  components: {
    CustomHeader,
    Contact
  },
  setup () {
    const router = useRouter()
    const modal = useModal()

    onMounted(() => {
      const token = window.localStorage.getItem('token')
      if (token) {
        router.push({ name: 'Feedback' })
      }
    })
    function handleLogin () {
      modal.open({
        component: 'ModalLogin'
      })
    }
    function handleAccountCreate () {
      modal.open({
        component: 'ModalCreateAccount'
      })
    }
    return {
      handleLogin,
      handleAccountCreate
    }
  }
}
</script>
