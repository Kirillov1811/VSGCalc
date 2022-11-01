<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Event</label>
            <input list="idEvent" 
                v-model="idEvent" 
                name="idEvent" 
            />
        </div>
        <datalist id="idEvent">
            <option value=""></option>
            <option value=""></option>
            <option value=""></option>
        </datalist>  

        <div class="form-control">
             <label>Work</label>
             <input list="idCosts" 
                v-model="idCosts" 
                name="idCosts" 
            />
        </div>
        <datalist id="idCosts">
            <option value=""></option>
            <option value=""></option>
            <option value=""></option>
        </datalist>  

        <div class="form-control">
            <label>Name</label>
            <input 
                type="text" 
                v-model="nameExpenses" 
                name="nameExpenses" 
                placeholder="Add Name Expenses" 
            />
        </div>
    </form>
  </template>
  
  <script>
    /* export default {
      name: 'AddReport',
      data() {
        return {
                   
          idEvent: '',
          idCosts: '',
          
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
    }  */
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