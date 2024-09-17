<template>
    <div>
        <h1>User Information</h1>
        <p><strong>Name: </strong> {{ userName }}</p>
        <p><strong>Address:</strong> {{ address }}</p>
        <p><strong>DOB: </strong>{{ dob }}</p>
        <button @click="calculateAge">Calculate Age</button>
        <p v-if="age !== null">{{ age }} years old</p>
        <button @click="validateAge">Validate Age</button>
        <p v-if="isValidated && age !== null && age < 18">You are under age</p>
        <p v-else-if="isValidated && age !== null && age >= 18">you are ok to use the website</p>
    </div>
</template>

<script>
export default {
    name: 'userDetail',
    data() {
        return {
            userName: 'Ashish',
            address: 'Connaught place, New Delhi',
            dob: '2000-05-18',
            age: null,
            isValidated: false
        }
    },
    methods: {
        calculateAge() {
            const dob = new Date(this.dob);
            const today = new Date();
            const diffInMiliSecond = today - dob;
            const age = Math.floor(diffInMiliSecond / (1000 * 60 * 60 * 24 * 365.25));
            this.age = age;
        },
        validateAge() {
            if (this.age === null) {
                this.calculateAge();
            }
            this.isValidated= true
        }
    }
}
</script>