<script setup lang="ts">
import { useUserStore } from '@/stores/user';
import { storeToRefs } from 'pinia';
import { onMounted } from 'vue';
const user = useUserStore();
const { users } = storeToRefs(user);
const { getAllUsers } = user;
onMounted(() => {
  getAllUsers();
});


console.log(users.value);

</script>

<template>
  <div class="container mt-4">
    <h1>AMBIL DARI AIRTABLE</h1>

    <table class="table table-bordered">
      <thead>
        <tr>
          <th>#</th>
          <th>Name</th>
          <th>Status</th>
          <th>Label</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.fields.Name">
          <td>{{ user.fields.Name }}</td>
          <td>{{ user.fields.Status }}</td>
          <td>{{ user.fields.Label }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>