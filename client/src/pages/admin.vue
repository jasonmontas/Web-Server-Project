<script setup lang="ts">
import { getAll, type User } from '@/models/users'
import { ref } from 'vue'

const users = getAll()
</script>

<template>
  <h1 class="title">Admin</h1>
  <table class="table">
    <thead>
      <tr>
        <th>ID</th>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Email</th>
        <th>Handle</th>
        <th>Role</th>
      </tr>
    </thead>
    <tfoot>
      <tr>
        <th>ID</th>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Email</th>
        <th>Handle</th>
        <th>Role</th>
      </tr>
    </tfoot>
    <tbody v-for="user in users.items" :key="user.id">
      <tr>
        <td>{{ user.id }}</td>
        <td>{{ user.firstName }}</td>
        <td>{{ user.lastName }}</td>
        <td>{{ user.email }}</td>
        <td>{{ user.username }}</td>
        <td>{{ user.role }}</td>
        <td>
          <button class="button"><i class="fa-solid fa-pen-to-square"></i></button>
        </td>
        <td>
          <button class="button"><i class="fa-solid fa-trash"></i></button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style>
title {
  font-size: 2rem;
  text-align: center;
}
</style>
