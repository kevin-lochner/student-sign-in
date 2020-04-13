<template>
    <tr v-bind:class="'present-' + student.present">
        <td>>{{student.name}}</td>
        <td>{{student.starID}}</td>
        <td><input type="checkbox" v-model="student.present" v-on:change="checked(student)"></td>
        <td v-show="editTable">
            <img class="delete-icon" v-on:click="deleteStudent(student)" src="@/assets/delete.png">
        </td>
    </tr>
</template>

<script>
export default {
    name: "StudentRow",
    props: {
        student: Object,
        editTable: Boolean
    },
    methods: {
        checked(student) {
            this.$emit('student-present', student)
        },
        deleteStudent(student) {
            if(confirm(`Are you sure you want to delete ${student.name}?`)) {
                this.$emit('delete-student', student)
            }
        }
    }
}
</script>

<style>

.present-true {
    color: gray;
    font-style: italic;
}

.present-false {
    font-weight: bold;
}


.delete-icon {
    height: 20px;
}


</style>