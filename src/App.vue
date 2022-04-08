<script setup lang="ts">
import { useAuthStore } from '@/stores/login';
import { storeToRefs } from 'pinia';
import { useRouter } from 'vue-router';
const auth = useAuthStore();
const { user } = storeToRefs(auth);
const router = useRouter();
const logout = () => {
  auth.logout();
  router.push('/');
};
</script>
<template>  
 
<div id="wrapper">

        <!-- Sidebar -->
        <div id="sidebar-wrapper">
            <ul class="sidebar-nav">
                <li class="sidebar-brand">
                    <router-link to="/">Dashboard</router-link>
                </li>
                <li>
                    <router-link to="/user">GET API</router-link>
                </li>
                <li>
                     <router-link to="/login" v-if="user?.email === 'dika@dika.com'">logout</router-link>
                    <router-link to="/login" v-else>login</router-link>
                </li>
                <li>
                    <router-link to="/todo">todo</router-link>
                </li>
            </ul>
        </div>
<!-- ATASAN NAVBAR-->
        <nav class="sb-topnav navbar navbar-expand navbar-dark bg-dark">
<!-- Navbar Search-->
            <form class="d-none d-md-inline-block form-inline ms-auto me-0 me-md-3 my-2 my-md-0">
                <div class="input-group">
                    <input class="form-control" type="text" placeholder="Search for..." aria-label="Search for..." aria-describedby="btnNavbarSearch" />
                    <button class="btn btn-primary" id="btnNavbarSearch" type="button"><i class="fas fa-search"></i></button>
                </div>
            </form>
        </nav>
<!-- /#sidebar-wrapper -->

<!-- Manggil Konten -->
         <router-view />
<!-- selesai manggil kontent -->

</div>

</template>

<script lang="ts">
import 'https://use.fontawesome.com/releases/v6.1.0/js/all.js'
export default {};
</script>

<style>
@import url('https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css');
@import url('https://fonts.googleapis.com/css?family=Roboto:300,400,400i,500');
@import './assets/css/style.css';
</style>
