<template>
    <div id="app">
        <ul>
            <li v-for="user in users" v-bind:key="user.id">
                {{ user.id }} {{ user.name }} - {{ user.email }}
            </li>
        </ul>
        <CreateUserForm />
    </div>
</template>

<script>
    import axios from "axios";
    import CreateUserForm from "./CreateUserForm";

    export default {
        name: 'app',
        components: {
            CreateUserForm
        },
        data() {
            return {
                users: []
            }
        },
        mounted() {
            axios
                .get("/api/users")
                .then(response => (this.users = response.data))
        },
    }
</script>

<style>
</style>
