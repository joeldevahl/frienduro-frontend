<template>
    <div>
        <div>
            <h2>Name</h2>
            <input type="text" v-model="name" />
        </div>

        <div>
            <h2>E-Mail</h2>
            <input type="text" v-model="email" />
        </div>

        <div>
            <h2>Submit</h2>
            <input type="submit" value="Submit" v-on:click="submit" />
        </div>
    </div>
</template>

<script>
    import axios from "axios";

    export default {
        name: "CreateUserForm",
        components: {},
        data() {
            return {
                name: '',
                email: ''
            }
        },
        methods: {
            submit() {
                const { name, email } = this;
                var userData = {
                    id: 0,
                    name: name,
                    email: email
                }
                window.console.log(JSON.stringify(userData));
                axios.post("/api/users", userData)
                    .then(function (response) { window.console.log(response) })
                    .catch(function (error) { window.console.log(error) })
            }
        }
    }
</script>

<style scoped>
</style>