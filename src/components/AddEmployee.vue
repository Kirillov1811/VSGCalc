<template>
  <form @submit="onSubmit" class="add-form">
    
    <div class="form-control">
      <label>Department</label>
      
      <input list="idDepartment" 
        v-model="idDepartment" 
        name="idDepartment" 
      />
      <datalist id="idDepartment">
          <option value="video"></option>
          <option value="sound"></option>
          <option value="Light"></option>
      </datalist>  
    </div> 

    <div class="form-control">
      <label>Name</label>
      <input 
        type="text" 
        v-model="nameEmployee" 
        name="nameEmployee" 
        placeholder="Add Name" />
    </div>
    <div class="form-control">
      <label>Last Name</label>
      <input
        type="text"
        v-model="lastNameEmployee"
        name="lastNameEmployee"
        placeholder="Add Last Name"
      />
    </div>
    <div class="form-control">
      <label>Phone Employee</label>
      <input
        type="tel"
        v-model="phoneEmployee"
        name="phoneEmployee"
        placeholder="Add Phone"
      />
    </div>
    <input type="submit" value="Save New Employee" class="btn btn-block" />
  </form>
</template>

<script>
  export default {
    name: 'AddEmployee',
    data() {
      return {       
        idDepartment: '',
        nameEmployee: '',
        lastNameEmployee: '',
        phoneEmployee: '',
      }
    },
    methods: {
      onSubmit(e) {
        e.preventDefault()

                //if(!this.nameEmployee) {
                  //  alert ('Please add a employee')
                    //return
               // }
        const newEmployee = {
          idDepartment: this.idDepartment,
          nameEmployee: this.nameEmployee,
          lastNameEmployee: this.lastNameEmployee,
          phoneEmployee: this.phoneEmployee,  
        }   
        
        this.$emit('add-employee', newEmployee)

        this.idDepartment = ''
        this.nameEmployee = ''
        this.lastNameEmployee = ''
        this.phoneEmployee = '' 
      },
    },
  }
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>