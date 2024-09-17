<template>
    <div>
        <h1>User Information</h1>
        <p><strong>Name: </strong> {{ userName }}</p>
        <p><strong>Address:</strong> {{ address }}</p>
        <p><strong>DOB: </strong>{{ dob }}</p>
        <button @click="calculateAge">Calculate Age</button>
        <p v-if="age !== null">{{ age }} years old</p>
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
            age: null
        }
    },
    methods: {
        calculateAge() {
            const dob = new Date(this.dob);
            const today = new Date();
            let age = today.getFullYear() - dob.getFullYear();
            const MonthDiff = today.getMonth() - dob.getMonth();

            if (MonthDiff < 0 || MonthDiff === 0 && today.getDate() < dob.getDate()) {
                age--;
            }
            this.age = age;
        }
    }
}
</script>