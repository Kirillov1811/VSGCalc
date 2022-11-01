<template>
    <div    :key="employee.id" 
            v-for="employee in employees">
        <Employee 
            @delete-employee="$emit('delete-employee',employee.id)"
            :employee="employee"/>
    </div>
</template>

<script>
    import Employee from './Employee.vue'

    export default {
        name: 'Employees',
        props: {
            employees: Array
        },
        components: {
            Employee
        },
        emits: ['delete-employee'],
    }
</script>