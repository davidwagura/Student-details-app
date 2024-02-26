<template>
  <div class="container mt-5">
      <div class="card">
          <div class="card-header">
             <h4>Edit Student</h4> 
          </div>
          <div class="card-admission_number">
              <div class="mb-3">
                  <form>
                      <div>
                          <label for="first_name">First Name:</label>
                          <input type="text" id="first_name" class="form-control" v-model="formData.first_name" />
                      </div>
                      <div>
                          <label for="admission_number">Last Name:</label>
                          <input id="admission_number" class="form-control" v-model="formData.last_name">
                      </div>
                      <div>
                          <label for="age">Age:</label>
                          <input id="age" class="form-control" v-model="formData.age">
                      </div>
                      <div>
                          <label for="admission_number">Admission Number:</label>
                          <input id="admission_number" class="form-control" v-model="formData.admission_number">
                      </div>

              
                      <button type="button" @click="updateForm()">Update</button>
                  </form>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
name: 'EditItem',

data() {
  return {
    formData: {
      first_name: '',
      last_name: '',
      age: '',
      admission_number: '',


      },
  };
},
created() {
    const id = this.$route.params.id;
    axios.get(`http://127.0.0.1:8000/api/student/${id}`)
    .then(response => {
      // console.log('response');
        let res = response.data;
        this.formData.first_name = res.first_name;
        this.formData.last_name = res.last_name;
        this.formData.age = res.age;
        this.formData.admission_number = res.admission_number;

        });
  },
  methods: {

    updateForm() {
      const id = this.$route.params.id;
      axios.put(`http://127.0.0.1:8000/api/student/${id}`, this.formData)
        .then(response => {
          this.formData.first_name = response.data.first_name;
          this.formData.last_name = response.data.last_name;
          this.formData.age = response.data.age;
          this.formData.admission_number = response.data.admission_number;
          console.log(response.data)
        });
        this.$router.push('/');
    }

  },
};

</script>

  
