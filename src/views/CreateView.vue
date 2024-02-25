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
                            <input type="text" id="first_name" v-model="formData.first_name" />
                        </div>
                        <div>
                            <label for="admission_number">Last Name:</label>
                            <textarea id="admission_number" v-model="formData.admission_number"></textarea>
                        </div>
                        <div>
                            <label for="age">Age:</label>
                            <input id="age" v-model="formData.age">
                        </div>
                        <div>
                            <label for="admission_number">Admission Number:</label>
                            <textarea id="admission_number" v-model="formData.admission_number"></textarea>
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
  name: 'CreatItem',
  
  data() {
    return {
      formData: {
        first_name: '',
        admission_number: '',
        age: '',
        admission_number: '',


        },
    };
  },
  methods: {
    submitForm() {
      axios.post('http://127.0.0.1:8000/api/student', this.formData)
      .then(response => {
        console.log('response');
        
          this.formData.first_name = ""
          this.formData.admission_number = ""
          this.formData.age = ""
          this.formData.admission_number = ""

        
        return response
      });
    }
  }

}  
</script>

    
