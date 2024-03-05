<template>
    <div @click.self="startButtonClickedStatusChanged" class="content">
        <div id="popupId" class="popup" v-if="startButtonClicked">
            <div class="popup_content">
                <h2>Попап для ввода данных</h2>
                <input id="name" type="text" placeholder="Имя" v-model="resultObj.name">
                <input id="surname" type="text" placeholder="Фамилия" v-model="resultObj.surname">
                <input id="patronymic" type="text" placeholder="Отчество" v-model="resultObj.patronymic">
                <input id="email" type="text" placeholder="Почта" v-model="resultObj.email">
                <input id="phone" type="text" placeholder="Номер телефона" v-model="resultObj.phone">
            </div>
            <button class="popup_button" type="submit" @click="formatResultObjToJSON">Отправить</button>
        </div>
        <div class="start" v-else>
            <button class="start_button"  @click="startButtonClickedStatusChanged">Начать</button>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                startButtonClicked: false,
                resultObj : {
                    name: '',
                    surname: '',
                    patronymic: '',
                    email: '',
                    phone: '',
                },
                result: '',
            }
        },
        methods: {
            startButtonClickedStatusChanged(e) {
                e.stopPropagation();
                this.startButtonClicked = !this.startButtonClicked;
            },
            formatResultObjToJSON() {
                this.result = JSON.stringify(this.resultObj);
                this.$emit('formatToJSON', {
                    result: this.result
                })
            },
        }
    }
</script>

<style>
.content {
    height: 100vh;
}
</style>