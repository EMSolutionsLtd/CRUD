<template>

    <div class="container mt-5">
        <div class="card">
            <div class="card-header">
                <h4>Add Students</h4>
            </div>
            <div class="card-body">

                <ul v-if="Object.keys(this.errorList).length > 0" class="alert alert-warning">
                    <li v-for="(error, index) in this.errorList" :key="index" class="mb-0 ms-3">
                        {{ error[0] }}
                    </li>
                </ul>

                <div class="mb-3">
                    <label for="">Name</label>
                    <input type="text" v-model="model.student.name" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="">Course</label>
                    <input type="text" v-model="model.student.course" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="">Email</label>
                    <input type="text" v-model="model.student.email" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="">Phone</label>
                    <input type="text" v-model="model.student.phone" class="form-control">
                </div>
                <div class="mb-3">
                    <button type="button" @click="saveStudent" class="btn btn-primary">Save</button>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
import axios from 'axios';

export default {
    name: 'studentCreate',
    data(){
        return {
            errorList: '',
            model: {
                student: {
                    name: '',
                    course: '',
                    email: '',
                    phone: ''
                }
            }
        }
    },
    methods: {
        saveStudent(){
            var mythis = this;
            axios.post('http://127.0.0.1:8000/api/students', this.model.student).then(res => {
                console.log(res.data);
                alert(res.data.message);

                this.model.student = {
                    name: '',
                    course: '',
                    email: '',
                    phone: ''
                }

                this.errorList = '';
            })
            .catch(function(error) {
                if(error.response) {
                    if(error.response.status == 422) {
                        mythis.errorList = error.response.data.errors;
                    }
                    // console.log(error.response.data);
                    // console.log(error.response.status);
                    // console.log(error.response.headers);
                } else if(error.request) {
                    console.log(error.request);
                } else {
                    console.log('Error', error.message);
                }
            });
        },
    },
}
</script>