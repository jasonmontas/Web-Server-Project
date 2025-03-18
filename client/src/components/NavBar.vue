<script setup lang="ts">
import { ref } from 'vue'

const isActive = ref(false)
</script>

<template>
  <nav class="navbar is-info" role="navigation" aria-label="main navigation">
    <div class="container">
      <div class="navbar-brand">
        <RouterLink to="/" class="navbar-item">
          <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="30" />
        </RouterLink>
        <RouterLink to="/workouts" class="navbar-item">My Workouts</RouterLink>
        <RouterLink to="/social" class="navbar-item">Social</RouterLink>

        <a
          role="button"
          class="navbar-burger"
          aria-label="menu"
          aria-expanded="false"
          :class="{ 'is-active': isActive }"
          @click="isActive = !isActive"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div class="navbar-menu" :class="{ 'is-active': isActive }">
        <div class="navbar-start">
          <div class="navbar-item has-dropdown is-hoverable">
            <a class="navbar-link"> More </a>

            <div class="navbar-dropdown">
              <RouterLink to="/admin" class="navbar-item"> Admin </RouterLink>
            </div>
          </div>
        </div>

        <div class="navbar-end">
          <div class="navbar-item">
            <div class="buttons">
              <a class="button is-primary">
                <strong>Sign up</strong>
              </a>
              <div class="navbar-item has-dropdown is-hoverable">
                <a class="button is-light navbar-link"> Log in </a>

                <div class="navbar-dropdown">
                  <a class="navbar-item"> Emily Johnson </a>
                  <a class="navbar-item"> Abigail </a>
                  <a class="navbar-item"> Madison </a>
                  <hr class="navbar-divider" />
                  <a class="navbar-item"> Other User </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped></style>
