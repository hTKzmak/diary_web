<template>
    <div class="form">
        <div class="input-form">
            <div class="select-form">
                <select name="select-day" id="day" v-model="dayValue">
                    <option value="ПН">Понедельник</option>
                    <option value="ВТ">Вторник</option>
                    <option value="СР">Среда</option>
                    <option value="ЧТ">Четверг</option>
                    <option value="ПТ">Пятница</option>
                    <option value="СБ">Суббота</option>
                    <option value="ВС">Воскресенье</option>
                </select>
                <select name="select-importance" id="importance" v-model="importanceValue">
                    <option value="true">Срочно</option>
                    <option value="false">Не срочно</option>
                </select>
            </div>
            <input type="text" name="input-description" id="description" value="Описание" v-model="descriptionValue">
        </div>
        <div class="button-submit">
            <button @click="handle(dayValue, importanceValue, descriptionValue)">Добавить</button>
        </div>
    </div>
</template>
  
<script>
export default {
    data(){
        return{
            dayValue: 'ПН',
            importanceValue: 'true',
            descriptionValue: 'Описание'
        }
    },
    methods: {
        handle(day, important, title) {
            this.$emit('handle', day, important, title)
        }
    }
}
</script>
  
<style>
.form {
    display: flex;
    justify-content: space-between;
    align-items: end;

    background-color: #ECF0F1;
    border: 1px solid #000;
    border-radius: 20px;

    padding: 30px 60px;

    box-shadow: 0px 4px 4px 0px #00000040;
}

select {
    width: 253px;
    height: 45px;
}

.select-form {
    display: flex;
    gap: 34px;
}

#description {
    margin-top: 24px;
    width: 534px;
    height: 45px;
}

.input-form {
    display: grid;
    gap: 24px;
}

button {
    width: 163px;
    height: 45px;
    color: #fff;
    font-size: 20px;
    border: 1px solid #000;
    background-color: #1ABC9C;
    border-radius: 23px;
}

button:active {
    background-color: #178871;
}
</style>
  