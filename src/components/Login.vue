<template>
    <div></div>
</template>

<script>
import {mapActions} from 'vuex';
export default {
    data: () => ({
        username: "",
        password: "",
        email: "",
        error: ""
    }),
    methods: {
        ...mapActions({
            loginVue: "auth/login"
        }),
        async login() {
            try {
                await this.loginVue({
                    username: this.username,
                    password: this.password
                })
            } catch (error) {
                this.error = error;
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    
</style>