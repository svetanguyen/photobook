<template>
    <div>
        <h3>
            
        </h3>
    </div>
</template>

<script>
export default {
    data: () => ({
        username: '',
        password: '',
        email: '',
        error: '',
        confirmPassword: '',
        code: ''
    }),
    methods: {
        async signUp() {
            if(!this.email || !this.password) {
                return;
            }
            try {
                await this.$store.dispatch('auth/signUp', {
                    username: this.username,
                    password: this.password,
                    email: this.email
                });

                this.confirmPassword = true;
            } catch(error) {
                this.error = error;
            }
        },
        async confirmSignUp() {
            if (!this.username || !this.code) {
                return;
            }

            try {
                await this.$store.dispatch('auth/confirmSignUp', {
                    username: this.username,
                    code: this.code
                });
                await this.$store.dispatch('authlogin', {
                    username: this.username,
                    password: this.password
                });
                this.$router.push('/albums');

            } catch(error) {
                console.log(error);
                this.error = error;
            }
        }
    }
}
</script>