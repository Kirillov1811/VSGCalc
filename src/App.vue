<template>
  <div            class="container">
    <Header       title="Employee"/>
  
    <AddEmployee  @add-employee="addEmployee"/>
    <Departments  @delete-employee="deleteDepartment"
                  :departments="departments"/>
    <Employees 
                  @delete-employee="deleteEmployee"
                  :employees="employees" />
  </div>
</template>

<script>
  import Header from './components/Header';
  import Employees from './components/Employees';
  import AddEmployee from './components/AddEmployee';
  import Report from './components/Report.vue';
  import Departments from './components/Departments.vue';
  
    export default {
      name: 'App',
      components: {
        Header,
        Employees,
        AddEmployee,
        Report,
        Departments,   
      },

      data(){
        return {
          employees: [],
          //departments: []
        }
      },
      methods: {
        async  addEmployee(employee) {
          
          const res = await fetch('/api/employee', {
              method: 'POST',
              headers: {
                'Accept': 'application/json',
                'Content-Type': 'application/json'
              },
              body: JSON.stringify(employee),
          })

          const data = await res.json()
          employee.id = data.id
          this.employees = [...this.employees, employee] 
        },


        async deleteEmployee(id) {
          if (confirm('Are you sure? ')) {
              const res = await fetch(`/api/employee/${id}`,
              {
              method: 'DELETE'
              })
              res.status === 200 ? (
              this.employees = this.employees.filter((employee) => employee.id !== id))
               : alert('Error deleting employee') 
          }
        },

        async fetchEmployees() {
          const res = await fetch('/api/employee')
          const data = await res.json()
          return data 
        },


        async fetchEmployee(id) {
          const res = await fetch(`/api/employee/${id}`)
          const data = await res.json()
          return data 
        }, 
      
       
        async created() {
        this.employees = await this.fetchEmployees()  
        },   
      }
    }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
