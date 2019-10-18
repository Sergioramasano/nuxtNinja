<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <nuxt-link class="navbar-brand" to="/">Nuxt SSR</nuxt-link>

    <div
      class="collapse navbar-collapse"
      id="navbarSupportedContent"
    >
      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <nuxt-link
            exact
            no-prefetch
            active-class="active"
            class="nav-link"
            to="/"
          >
            Home
            <span
              class="sr-only">(current)
            </span>
          </nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link
            active-class="active"
            class="nav-link"
            to="/about">
            About
          </nuxt-link>

        </li>
        <li class="nav-item">
          <nuxt-link
            active-class="active"
            class="nav-link"
            to="/users">
            Users
          </nuxt-link>
        </li>
        <li
          v-if="!hasToken"
          class="nav-item">
          <nuxt-link
            active-class="active"
            class="nav-link"
            to="/login">
            login
          </nuxt-link>
        </li>
        <li class="nav-item" v-else>
          <a
            @click.prevent="logout"
            active-class="active"
            class="nav-link"
            href="#"
           >
            Logout
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
    export default {
        name: "Navbar",
        computed:{
          hasToken(){
              return this.$store.getters.hasToken
          }
        },
        methods:{
            logout(){
                this.$store.dispatch('logout');
                this.$router.push('/login')
            }
        }
    }
</script>

<style scoped>

</style>
