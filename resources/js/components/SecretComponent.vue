<template>
    <div class="container">
        <!--login form-->
        <div class="row mt-4">
            <div class="col-6 offset-3">
                <form action="#" @submit.prevent="handleLogin">
                <h3>Sign In for Secrets</h3>
                    <div class="form-row">
                        <input type="email" name="email" class="form-control" v-model="formData.email" placeholder="Email Address">
                    </div>
                    <div class="form-row">
                        <input type="password" name="password" class="form-control" v-model="formData.password" placeholder="password">
                    </div>
                    <div class="form-row">
                        <button type="submit" class="btn btn-primary">Sign in</button>
                    </div>
                </form>
            </div>
        </div>
        <!--secrets list-->
    </div>
</template>

<script>
    export default {
        data(){
            return{
                secrets:[],
                formData:{
                    email:'',
                    password:''
                }
            }
        },
        methods:{
            handleLogin(){
                //send axios request to the login route
                axios.get('/sanctum/csrf-cookie').then(response=>{
                    axios.post('/login',this.function).then(response=>{
                        console.log(response);
                    });
                });
            }
        }
    }
</script>

<style>
    .form-row
    {
        margin-bottom:10px;
    }
</style>
