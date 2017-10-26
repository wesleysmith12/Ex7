<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <!-- Part 1 5 Points-->
                    <!-- Create a Signup Form where you retrieve the following Information -->
                    <!-- Full Name (First Name + Last Name) -->
                    <div class="form-group">
                        <div>
                            <app-name v-model="fullName"></app-name>
                        </div>
                    </div>

                    <!--<div class="form-group">-->
                        <!--<label for="lastName">First Name</label>-->
                        <!--<input-->
                                <!--type="text"-->
                                <!--id="lastName"-->
                                <!--class="form-control"-->
                                <!--v-model="firstName">-->
                        <!--<p>{{ firstName }}</p> </div>-->
                    <!--<div class="form-group">-->
                        <!--<label for="firstName">Last Name</label>-->
                        <!--<input-->
                                <!--type="text"-->
                                <!--id="firstName"-->
                                <!--class="form-control"-->
                                <!--v-model="lastName">-->
                        <!--<p>{{ lastName }}</p> </div>-->
                    <!-- Mail -->
                    <div class="form-group">
                        <label for="email">Mail</label>
                        <input
                                type="text"
                                id="email"
                                class="form-control"
                                v-model="email">
                    </div>
                    <!-- Password -->
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                                type="password"
                                id="password"
                                class="form-control"
                                v-model.lazy.trim.number="password">
                    </div>
                    Store Data?
                    <div class="form-group">
                            <label for="yes">
                                <input
                                        type="radio"
                                        id="yes"
                                        value="Yes"
                                        v-model="storedata"> Yes
                            </label>
                            <label for="no">
                                <input
                                        type="radio"
                                        id="no"
                                        value="No"
                                        v-model="storedata"> No
                            </label>
                    </div>

                    <hr>
                    <div class="form-group">
                        <div>
                            <button
                                    class="btn btn-primary"
                                    @click.prevent="submitted">Submit!
                            </button>
                        </div>
                    </div>

                    <!-- Part 2 5 Points -->
                    <!-- Only display the Form if it has NOT been submitted -->
                    <!-- Display the Data Summary ONCE the Form HAS been submitted -->

                    <!-- Part 3 5 Points -->
                    <!-- Edit the Example from above and create a custom "Full Name" Control -->
                    <!-- which still holds the First Name and Last Name Input Field -->
                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-if="isSubmitted">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Full Name: {{ fullName }}</p>
                        <p>Mail: {{ email }} </p>
                        <p>Password: {{ password }} </p>
                        <p>Store in Database?: {{ storedata }} </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    import Name from './Name.vue';

    export default {
        data() {
            return {
//                firstName: '',
//                lastName: '',
                fullName: '',
                email: '',
                password: '',
                storedata: 'Yes',
                isSubmitted: false,

            }
        },
        methods: {
            submitted() {
                if(this.storedata === 'Yes'){
                    this.isSubmitted = true;
                }else {
                    this.isSubmitted = false;
                }
            }
        },components: {
            appName : Name
        }
    }
</script>

<style>
</style>
