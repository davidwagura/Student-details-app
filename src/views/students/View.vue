<template>
    <div class="card">
        <div class="card-header">
            <h4>
                Students
                <router-link to="/student/create" class="btn btn-primary float-end">
                    Add Student
                </router-link>
            </h4>
        </div>
        <div class="card-body">
            <table class="table table-bordered">
                <thead>
                    <th>First Name</th>
                    <th>Last Name</th>
                    <th>Gender</th>
                    <th>Admission Number</th>
                    <th>Home County</th>
                    <th>Year Of Birth</th>
                    <th>Action</th>
                </thead>
                <tbody>
                    <tr>
                        
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>
  
<script>
import axios from 'axios'

export default {
    name: 'students',
    data() {
        return {
            students: []
        }
    },
    mounted(){
        this.getStudents();
        // console.log('THE STUDENTS');
    },
    methods: {
        getStudents() {
            axios.get(`http://127.0.0.1:8000/api/students`).then( res => {  
                console.log(res)
            })
        }
    },
}
</script>