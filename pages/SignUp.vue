<script setup>

const form = reactive({
    fullName: '',
    phone: '',
    age: '',
    course: '',
    consent: false
})

const courses = [
    'Цифровая живопись',
    'Scratch',
    'Основы Java',
    'Web разработка'
];

const submitForm = () => {

    console.log(
        form
    )
};


let response = await fetch("https://api.formtomail.ru/send", {
    method: "POST",
    mode: "cors",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        title: "Новая заявка", // Заголовок письма
        body: {   // Содержимое формы (можно прислать HTML)
            "Имя": "значение поля",
            "Телефон": "значение поля"
        },
        apiKey: "VmsveCwkahmAI2B3"
    })
});
let body = await response.json();

</script>

<template>
    <v-container>
        <v-row class="d-flex justify-center">
            <v-col  cols="12" md="6" sm="8" lg="4">
                <v-card class=" pa-4 pa-md-8">

                    <h3 class="text-center"color="error">Запись</h3>


                    <v-text-field type="text" v-model="form.fullName" placeholder="Фамилия Имя" />

                    <v-text-field type="tel" v-model="form.phone" placeholder="Телефон" />



                    <v-text-field type="number" v-model="form.age" placeholder="Возраст, лет" />


                    <v-autocomplete label="Выбрать курс" v-model='form.course' :items="courses"></v-autocomplete>

                    <v-checkbox label="Я даю согласие на обработку персональных данных"
                        v-model="form.consent"></v-checkbox>

                    <div class="d-flex justify-center">
                        <v-btn color="error" @click="submitForm">
                            Записаться
                        </v-btn>
                    </div>

                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<style scoped></style>