<template>
    <div class="task-list" v-for="elem in data">
        <div class="task-item">
            <div class="delete-button" @click="deleteDay(elem.id)">
                <div class="line line-one"></div>
                <div class="line line-two"></div>
            </div>
            <div class="day">{{ elem.dayName }}</div>
            <div class="task-item-list">
                <div v-for="info in elem.tasks" class="task-info">
                    <div class="delete-button" @click="deleteItem(info.id)">
                        <div class="line line-one"></div>
                        <div class="line line-two"></div>
                    </div>

                    <div :class="[info.necessary == 'true' ? 'task necessary' : 'task not-necessary']" @click="deleteItem(info.id)">
                        {{ info.description }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: ['data', 'deleteItem', 'deleteDay']
}
</script>
  
  
<style>
.task-list {
    margin-top: 43px;
    display: grid;
    row-gap: 23px;
}

.task-item {
    display: flex;
    position: relative;
}

.day {
    display: flex;
    justify-content: center;
    align-items: center;

    font-size: 30px;
    text-align: center;

    color: #fff;
    background-color: #34495E;

    width: 80px;
    border-bottom-left-radius: 20px;
    border-top-left-radius: 20px;
}

.task-item-list {
    background-color: #ECF0F1;
    border-bottom-right-radius: 20px;
    border-top-right-radius: 20px;
    width: 100%;
}

.task-item-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: left;
}

.task {
    margin-top: 10px;
    margin-bottom: 10px;
    margin-left: 17px;
    padding: 5px 10px;
    font-size: 30px;
    color: #fff;
}

.not-necessary {
    background-color: #1ABC9C;
}

.necessary {
    background-color: #E74C3C;
}

.task-info {
    position: relative;
}

.task-info>.delete-button {
    position: absolute;
    top: -5px;
    right: -15px;
}

.task-item>.delete-button {
    position: absolute;
    top: -15px;
    right: -15px;
}
</style>
  