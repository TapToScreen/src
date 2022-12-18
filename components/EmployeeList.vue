<template>

    <div class="employees-list" v-for="(employee, index) in employees">
        <div class="employee">
        <span>Порядковый номер: {{index + 1}}</span> <br>
        <span>ФИО: {{employee.fullName}}</span> <br>
        <span>Дата выдачи зарплаты: {{employee.date}}</span> <br>
        <span>Количество отработанных дней: {{employee.daysWork}}</span> <br>
        <span>Сумма заработной платы сотрудника без налоговых отчислений: {{employee.salary}}$</span> <br>
        <span>Сумма заработной платы сотрудника с налоговыми отчислениями: {{Math.trunc(employee.salary - (employee.salary * 0.15))}}$</span> <br>
            <div class="remove">
                <button type="button" name="plus" class="btn btn-danger" @click="removeEmployee(index)">Удалить</button>
            </div>
        </div>
       </div> 
       
</template>
<script>
export default {
    props: {
        employees: {
            type: Array,
            required: true
        }
    },
    methods: {
        removeEmployee (index) {
            this.$emit("remove", this.employees, index)
        }
    }
}
</script>
<style scoped>
    
</style>


