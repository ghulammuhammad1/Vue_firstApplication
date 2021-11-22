<template>
  <form @submit.prevent="submit">
    <h2>Registration</h2>
    <Group
      name="name"
      label="Personal information"
    >
      <Text
        name="first_name"
        placeholder="First name"
        rules="required"
        columns="6" />

      <Text
        name="last_name"
        placeholder="Last name"
        rules="required"
        columns="6" />
    </Group>

    <Text
      name="email"
      placeholder="Email"
      rules="required|email|unique"
      label="Account information" />

    <Password
      name="password"
      placeholder="Password"
      rules="required|min:8|confirmed" />

    <Password
      name="password_confirmation"
      placeholder="Password again"
      rules="required" />

    <Toggle
      name="remember_me"
      text="Remember me" />

    <Button
      type="submit" 
      label="Submit" 
      class="btn-default" />
  </form>
</template>

<script>
  import { Vueform, useVueform } from 'vueform'

  export default {
    name:"SignUp",
    mixins: [Vueform],
    setup: useVueform,
    data: () => ({
      endpoint: '/api/v1/user',
      method: 'POST'
    }),
    mounted() {
      this.on('success', () => {
        console.log(this.data)
        alert('Registration successful')
        this.reset()
      })
    }
  }
</script>