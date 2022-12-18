<template>

    <div class="add-employee">
    
    <label for="" class="form-label">ФИО:</label>
    <input type="text" class="form-control" id="name" aria-describedby="helpId" v-model.value="employees.inputFullName">

    <label for="" class="form-label">Дата выдачи зарплаты:</label>
    <input type="date" class="form-control" id="date" aria-describedby="helpId" v-model.value="employees.inputDate">
  
    <label for="" class="form-label">Количество отработанных дней:</label>
    <input type="text" class="form-control" id="work" aria-describedby="helpId" v-model.value="employees.inputDaysWork">

    <label for="" class="form-label">Размер заработной платы сотрудника:</label>
    <input type="number" class="form-control" id="salary" aria-describedby="helpId" min="01-01,2022" v-model.value="employees.inputSalary">


    <br>

  
  </div>
<form>
    <div class="d-grid gap-2">
        <button type="button" class="btn btn-primary" @click="checkInput">Добавить сотрудника</button>
    </div>
</form>

</template>
<script>
export default {
    data() {
        return {
            employees: {
                inputFullName: "",
                inputDate: "",
                inputDaysWork: "",
                inputSalary: "",
            }
        }
    },
    methods: {
        checkInput () {
            this.$emit("check", this.employees)
        },

            // this.employees.push({
            //     fullName:this.employees.inputFullName,
            //     date:this.employees.inputDate,
            //     daysWork:this.employees.inputDaysWork,
            //     salary:this.employees.inputSalary,
            // })

            
        // this.inputFullName = "", this.inputDate = "", this.inputDaysWork = "", this.inputSalary = "";
        // this.solaryResult();
        
    },
}
</script>
<style scoped>
    .empty {
        border-color: red;
    }
</style>