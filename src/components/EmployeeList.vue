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
       <div class="total-salary">
        <div class="alert alert-primary" role="alert">
          Общая сумма заработных плат сотрудников без налоговых: <strong>{{ TotalResult }}$</strong>
        </div>
    </div>

    <div class="total-salaryWithNalog">
        <div class="alert alert-primary" role="alert">
          Общая сумма зарплаты: <strong>{{TotalWithNalogPrice}}$</strong>
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
    },
    computed: {
        TotalResult() {
            let result = []

            for (let item of this.employees) {
                result.push(item.salary)
            }

            result = result.reduce(function (sum, el){
                return sum + el 
            })

            return result
        },

        TotalWithNalogPrice () {
            let result = []

            for (let item of this.employees) {
                result.push(Math.trunc(item.salary - (item.salary * 0.15)))
            }

            result = result.reduce(function (sum, el){
                return sum + el 
            })

            return result
        }
    }
}
</script>
<style scoped>
    
</style>


