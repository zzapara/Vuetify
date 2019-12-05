<template>
    <v-container>
        <v-row>
            <v-col>
                <v-form ref="singUpForm"
                    v-model="formValidity">
                    <v-text-field 
                        label="Email"
                        type="email" 
                        v-model="email"
                        required
                        :rules="emailRules">
                    </v-text-field>
                    <v-autocomplete
                    label="Witch browser do you use?"
                    :items="browsers"
                    ></v-autocomplete>
                    <v-file-input lable="Attch profile photo">
                    </v-file-input>
                    <v-text-field lable="Birthday" v-model="birthday" readonly=""></v-text-field>
                    <v-date-picker v-model="birthday"></v-date-picker>
                    <v-checkbox label="Agree" v-model="agree" :rules="agreeRules"></v-checkbox>
                    <v-btn class="mr-4" color="primary" :disabled="!formValidity" type="submit">Submit</v-btn>
                    <v-btn class="mr-4" color="success" @click="validateForm">ValidateForm</v-btn>
                    <v-btn class="mr-4" color="warning" @click="restValidation">Reset validation</v-btn>
                    <v-btn class="mr-4" color="error" @click="resetForm">Reset</v-btn>
                </v-form>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    export default {
        data() {
            return {
                formValidity:false,
                agree:false,
                agreeRules:[
                    value => !!value || 'You must agree'
                ],
                email:'',
                emailRules:[
                    value => !!value || 'Email is required',
                    value => value.indexOf('@') !== 0 || 'Email should have name',
                    value => value.includes('@')  || 'Email should have @',
                    value => value.indexOf('.') - value.indexOf('@') > 1   || 'Email should contain a valid domain',
                    value => value.indexOf('.') <=  value.length -3 || 'Email should contain a valid domain extention'
                ],
                browsers:[
                    'Chrome',
                    'FireFox',
                    'Safari',
                    'Edge'
                ],
                birthday:''
            }
        },
        methods:{
            restValidation(){
                this.$refs.singUpForm.resetValidation()
            },
            resetForm(){
                this.$refs.singUpForm.reset()
            },
            validateForm(){
                this.$refs.singUpForm.validate()
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>