<template>
    <div :class="[]">
        <h3>{{employee.id}} {{employee.nameEmployee}} {{employee.lastNameEmployee}}
        <i @click="onDelete(employee.id)"
        class="fas fa-times"></i>    
        </h3> 
       
    </div>
    
</template> 

<script> 
    export default {
        name: 'Employee',
        props: {
            employee: Object
        },
        methods: {
            onDelete(id) {
                this.$emit('delete-employee', id)
            }
        }
    }
</script>

<style scope>
.fas {
  color: red;
}
.employee {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.employee.reminder {
  border-left: 5px solid green;
}
.employee h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>