<template>
    <div class="container mt-5">
        <div class="card">
            <div class="card-header">
               <h4>Add Student</h4> 
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

                
                        <button type="button" @click="submitForm()">Submit</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'CreatView',
  
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
  methods: {
    submitForm() {
      axios.post('http://127.0.0.1:8000/api/student ', this.formData)
      .then(response => {
        console.log(response.data);
        
        first_name = this.formData.first_name 
        last_name = this.formData.last_name 
        age = this.formData.age 
        admission_number = this.formData.admission_number 

        
        return response
      });
      this.$router.push('/');
    }
  }

}  
</script>

    
