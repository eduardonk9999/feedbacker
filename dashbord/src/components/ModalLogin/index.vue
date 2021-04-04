<template>
  <div>
    <div>
      <h1>Entre na sua conta</h1>
      <button @click="close" class="text-4xl text-gray-600 focus:outline-none">
        &times;
      </button>
    </div>

    <div class="mt-16">
      <form @submit.prevent="handleSubmit">
        <label class="block">
          <span class="text-lg font-medium text-gray-800">
            E-mail
          </span>
          <input
            v-model="state.email.value"
            :class="{
              'border-brand-danger': !!state.email.error-message
            }"
            type="email"
            class="block w-full px-4 mt-1 text-lg bg-gray-100 border-2 border-transparent rounded"
            placeholder="email@padraoemail.com"
          >
          <span
            v-if="!state.email.errorMessage"
            class="block font-medium text-brand-danger"
          >
            {{ state.email.errorMessage }}
          </span>
        </label>

        <label class="block">
          <span class="text-lg font-medium text-gray-800">
            Senha
          </span>
          <input
            v-model="state.password.value"
            :class="{
              'border-brand-danger': !!state.password.error-message
            }"
            type="password"
            class="block w-full px-4 mt-1 text-lg bg-gray-100 border-2 border-transparent rounded"
            placeholder="password"
          >
          <span
            v-if="!state.password.errorMessage"
            class="block font-medium text-brand-danger"
          >
            {{ state.password.errorMessage }}
          </span>
        </label>

        <button
          :disabled="state.isLoading"
          type="submit"
          :class="{
            'opacity-50': state.isLoading
          }"
          class="px-8 py-3 mt-10 text-2xl font-bold text-white rounded-full
          bg-brand-main focus:outline-none"
        >
          Entrar
        </button>
      </form>
    </div>
  </div>
</template>

<script>
import { reactive } from '@vue/reactivity'
import useModal from '../../hooks/useModal'

export default {
  setup () {
    const modal = useModal()

    const state = reactive({
      hasErros: false,
      isLoading: false,
      email: {
        value: '',
        erroMessage: ''
      },
      password: {
        value: '',
        errorMessage: ''
      }
    })

    // function handleSubmit () {
    //   console.log('login')
    // }

    return {
      state,
      close: modal.close
    }
  }
}
</script>
