<template>
    <div class="app"> 
        <EmployeeForm
            @check="checkInput"
        ></EmployeeForm>

        <EmployeeList 
            :employees="employees"
            @remove="removeEmployee"
        ></EmployeeList>

        <EmployeeResult
        :employees="employees"
            @price="totalPrice"
        ></EmployeeResult>
  </div>
</template>
<script>

import EmployeeForm from "@/components/EmployeeForm.vue";
import EmployeeList from "@/components/EmployeeList.vue";
import EmployeeResult from "@/components/EmployeeResult.vue";

export default {

    components: {
        EmployeeForm, EmployeeList, EmployeeResult
    },

    data() {
        return {
            employees: [
                {fullName: "Калугина Дарина Марковна", date: "17-10-2022", daysWork: 12, salary: 1200},
                {fullName: "Богданова Юлия Артёмовна", date: "01-10-2022", daysWork: 23, salary: 2500},
                {fullName: "Фролова Дарья Александровна", date: "22-09-2022", daysWork: 16, salary: 1700},
            ],
        }
    },
    methods: {

        addEmployee () {

        },


        checkInput (employees) {
            
            if (employees.inputFullName == "") {
                document.querySelector("#name").classList.add("empty")
                return
            }
            if (employees.inputDate == "") {
                document.querySelector("#name").classList.remove("empty")
                document.querySelector("#date").classList.add("empty")
                return
            }
            if (employees.inputDaysWork == "") {
                document.querySelector("#name").classList.remove("empty")
                document.querySelector("#date").classList.remove("empty")
                document.querySelector("#work").classList.add("empty")
                return
            }
            if (employees.inputSalary == "") {
                document.querySelector("#name").classList.remove("empty")
                document.querySelector("#date").classList.remove("empty")
                document.querySelector("#work").classList.remove("empty")
                document.querySelector("#salary").classList.add("empty")
                return
            }
            else 
                document.querySelector("#name").classList.remove("empty")
                document.querySelector("#date").classList.remove("empty")
                document.querySelector("#work").classList.remove("empty")
                document.querySelector("#salary").classList.remove("empty")
                this.employees.push({
                    fullName: employees.inputFullName,
                    date: employees.inputDate,
                    daysWork: employees.inputDaysWork,
                    salary: employees.inputSalary,
                });
                    employees.inputFullName = ""
                    employees.inputDate = ""
                    employees.inputDaysWork = ""
                    employees.inputSalary = ""
                    console.log(this.employees) 
                    
        },

        removeEmployee (employees, index) {
            employees.splice(index, 1)
            this.totalPrice()
        },

        totalPrice () {

        }
        
    },
}
</script>
<style>
    
</style>