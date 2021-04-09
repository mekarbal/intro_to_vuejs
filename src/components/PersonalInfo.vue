<template>
  <div>
   <div class="container mt-5">
    <div class="row justify-content-center">
      
      <div class="col-md-6">
       <h1>Personnal Information</h1>
         <form @submit="onSubmit" class="mt-5">
       <div class="form-group">
         <label for="name">Nom </label>
         <input type="text" v-model="form.name" name="name" id="name" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="lname">Prenom </label>
         <input type="text" v-model="form.lname" name="lname" id="lname" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="tel">Telephone </label>
         <input type="number" v-model="form.tel" name="tel" id="tel" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="cin">CIN </label>
         <input type="text" name="cin" v-model="form.cin" id="cin" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="passport">passport </label>
         <input type="text" name="passport" v-model="form.passport" id="passport" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="city">Ville </label>
         <input type="text" name="city" v-model="form.city" id="city" class="form-control" required>
       </div>
      
      <button type="submit" class='btn btn-primary btn-block mt-3'  @click="isHide=!isHide ">Add Info</button>
     </form>
      <div v-show="isHide" class="mt-5">
        {{dataPersonal}}
        <h1>Professional Information</h1>
         <form @submit="onSubmithandler">
       <div class="form-group">
         <label for="name">Email Pro </label>
         <input type="email" v-model="formPro.emailPro" name="name" id="name" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="employer">Employeur </label>
         <input type="text" v-model="formPro.employer" name="employer" id="employer" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="telP">Telephone pro </label>
         <input type="number" v-model="formPro.telP" name="telP" id="telP" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="cnss">CNSS </label>
         <input type="text" name="cnss" v-model="formPro.cnss" id="cnss" class="form-control" required>
       </div>
       <div class="form-group">
         <label for="addressPro">addressPro </label>
         <input type="text" name="addressPro" v-model="formPro.addressPro" id="addressPro" class="form-control" required>
       </div>
       
      <button type="submit" class='btn btn-primary btn-block mt-3'  data-toggle="modal" data-target="#exampleModal">Add Info</button>
      
     </form>
    
      </div>
      </div>
    </div>
   </div>
    <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">All Informations</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        <b>Infomations Personnelle</b>
        <p>Nom : <span>{{dataPersonal.name}}</span></p>
        <p>Prenom : <span>{{dataPersonal.lname}}</span></p>
        <p>Passport : <span>{{dataPersonal.passport}}</span></p>
        <p>CIN : <span>{{dataPersonal.cin}}</span></p>
        <p>City : <span>{{dataPersonal.city}}</span></p>
        <p>Telephone : <span>{{dataPersonal.tel}}</span></p>
        <hr/>
        <b>Infomations Professionnelle</b>
        
        <p>Email Pro : <span>{{dataPro.emailPro}}</span></p>
        <p>Address : <span>{{dataPro.addressPro}}</span></p>
        <p>Employeur : <span>{{dataPro.employer}}</span></p>
        <p>CNSS : <span>{{dataPro.cnss}}</span></p>
        <p>Telephone Pro : <span>{{dataPro.telP}}</span></p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
  </div>
</template>

<script>
     
  export default {
    name:'PersonalInfo',
    data() {
      
      return {
        dataPersonal:{},
        dataPro:{},
        form: {
          name: '',
          lname: '',
          passport: '',
          cin: '',
          city:'',
          tel:0
        },
        formPro: {
          emailPro: '',
          employer: '',
          addressPro: '',
          cnss: '',
          telP:0
        },
          isHide: false,
          
        
      }
    }
    ,
    methods: {
    onSubmit(event) {
        event.preventDefault()
        localStorage.setItem('personalInfo',JSON.stringify(this.form))
        
      },
      
    onSubmithandler(event) {
      event.preventDefault()
      console.log('Professional');
       localStorage.setItem('professionalInfo',JSON.stringify(this.formPro))
      this.dataPersonal = JSON.parse(localStorage.getItem('personalInfo'))
      this.dataPro = JSON.parse(localStorage.getItem('professionalInfo'))
      console.log(this.dataPersonal);
       
    }
     
    },
    
  }
</script>