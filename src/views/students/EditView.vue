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
                        <router-link :to="'/update/' + article.id">Edit</router-link>
                        </td>
                        <td>
                        <button @click="deleteItem()">Delete</button>
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
        formData: null
      };
    },

    created() {
      this.listStudents()
    },

      methods: {
        listStudents() {
          axios.get('http://127.0.0.1:8000/api/articles')
          .then(response => {
            console.log(response.data)
            this.formData = response.data;
            console.log(this.formData)
          });
        },
          deleteItem(id) {
            axios.delete(`http://127.0.0.1:8000/api/articles/${id}`)

            .then( response => {
              this.formData();
              return response
            })
          
        }
        
    }
  }
</script>