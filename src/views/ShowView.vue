<template>
  <div class="card">
      <div class="card-header">
          <h4>
              Students
              <router-link to="/create" class="btn btn-primary float-end">
                  Add Student
              </router-link>
          </h4>
      </div>
      <div class="card-body">
          <table class="table table-bordered">
              <thead>
                  <tr>
                      <th>Id</th>
                      <th>First Name</th>
                      <th>Last Name</th>
                      <th>Age</th>
                      <th>Admission number</th>
                      <th>Edit</th>
                      <th>Delete</th>
                  </tr>
              </thead>
              <tbody>
                  <tr v-for="student in students" :key="student">
                      <td>{{ student.id }}</td>
                      <td>{{ student.first_name }}</td>
                      <td>{{ student.last_name }}</td>
                      <td>{{ student.age }}</td>
                      <td>{{ student.admission_number }}</td>
                      <td>
                        <router-link :to="'/edit/' + student.id">Edit</router-link>
                      </td>
                      <td>
                        <button @click.prevent="deleteItem(student.id)">Delete</button>
                      </td>
                  </tr>
              </tbody>
          </table>
      </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'StudentsView',

  data() {
    return {
      students: []
  };
  },

  created() {
    this.listStudents()
  },

    methods: {
      listStudents() {
        axios.get('http://127.0.0.1:8000/api/student')
        .then(response => {
          // console.log(response.data)
          this.students = response.data;
          console.log(this.students);

        });
      },
      deleteItem(id) {
        axios.delete(`http://127.0.0.1:8000/api/student/${id}`)

        .then( response => {
        console.log(response);

        this.listStudents();
        })
          
      }

   },
        
}

</script>