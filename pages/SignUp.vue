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

const submitForm = async () => {
Object.keys(form).forEach(key => {
//   console.log(`Ключ: ${key}, Значение: ${form[key]}`);
if (!form[key]){
    console.log(key);
    
}
})
    // let req_body = {
    //     title: "Новая заявка", // Заголовок письма
    //     body: form,
    //     apiKey: "VmsveCwkahmAI2B3"
    // }
    // req_body.body.consent = req_body.body.consent ? 'да' : 'нет'
    // console.log(req_body)
    // let response = await fetch("https://api.formtomail.ru/send", {
    //     method: "POST",
    //     mode: "cors",
    //     headers: {
    //         "Content-Type": "application/json"
    //     },
    //     body: JSON.stringify(req_body)
    // });

    // let body = await response.json();
    // if (body.statusCode == 200) {
    //     snackbar.value = true
    // }
    // console.log(body.statusCode);

};

import { ref } from 'vue'

const snackbar = ref(false)
const snackbar1 = ref(true)

</script>

<template>
    <v-container>
        <v-row class="d-flex justify-center">
            <v-col cols="12" md="6" sm="8" lg="4">
                <v-card class=" pa-4 pa-md-8">

                    <h3 class="text-center" color="error">Запись</h3>


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


                    <!-- <div class="text-center orange-darken-2">


                        <v-snackbar v-model="snackbar" vertical>
                            <div class="text-subtitle-1 pb-2">Вы зарегестрировались!</div>

                            <p>Ждите звонка!</p>

                            <template v-slot:actions>
                                <v-btn color="indigo" variant="text" @click="snackbar = false">
                                    Close
                                </v-btn>
                            </template>
                        </v-snackbar>
                    </div> -->


<div class="text-center orange-darken-2">


                        <v-snackbar v-model="snackbar1" vertical>
                            <div class="text-subtitle-1 pb-2">Введите поле!</div>

                            <!-- <p>Поле нужно ввести</p> -->

                            <template v-slot:actions>
                                <v-btn color="indigo" variant="text" @click="snackbar = false">
                                    Close
                                </v-btn>
                            </template>
                        </v-snackbar>
                    </div>



                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<style scoped></style>
