<template>
    <div>
        <h1>User Information</h1>
        <p><strong>Name: </strong> {{ userName }}</p>
        <p><strong>Address:</strong> {{ address }}</p>
        <p><strong>DOB: </strong>{{ dob }}</p>
        <button @click="calculateAge">Calculate Age</button>
        <p v-if="age !== null">{{ age }} years old</p>
        <button v-if="age !== null" @click="validateAge">Validate Age</button>
        <p v-if="isValidated && age !== null && age < 18" :class="{ 'text-red': age < 18 }">You are under age</p>
        <p v-else-if="isValidated && age !== null && age >= 18" :class="{ 'text-green': age >= 18 }">you are ok to use
            the website</p>
        <h2>Users List</h2>
        <li v-for="(user, index) in users" :key="index">
            UserName: {{ user.Name }}, Age: {{ user.Age }}
        </li>
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
            isValidated: false,

            users: [
                { Name: 'rahul', Age: 24 },
                { Name: 'rohit', Age: 20 }
            ]
        };
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
            this.isValidated = true
        }
    }
}

</script>

<style scoped>
.text-red {
    color: red;
}

.text-green {
    color: green;
}

li {
    list-style: none;
}
</style>