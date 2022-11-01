<template>
    <div    :key="department.id" 
            v-for="department in departments">
        <Department 
            @delete-department="$emit('delete-department',department.id)"
            :department="department"/>
    </div>
</template>

<script>
    import Department from './Department.vue'

    export default {
        name: 'Departments',
        props: {
            departments: Array
        },
        components: {
            Department
        },
        emits: ['delete-department'],
    }
</script>