<template>
    <div>
        <h1>User Information</h1>
        <p><strong>Name: </strong> {{ userName }}</p>
        <p><strong>Address:</strong> {{ address }}</p>
        <p><strong>DOB: </strong>{{ dob }}</p>
        <button @click="calculateAge">Calculate Age</button>
        <p v-if="age">{{ age }} years old</p>
        <div v-show="age"> 
            <button @click="validateAge">Validate Age</button>
            <p v-if="isValidated  === true" class="success">You are ok to use the website</p>
            <p v-if="isValidated === false" class="error">You are under age</p>
        </div>

        <h2>Users List</h2>
        <li v-for="(user, index) in users" :key="index">
            <strong>UserName: </strong> {{ user.Name }}, <strong>Age:</strong> {{ user.Age }}
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
            isValidated: null, 

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
            this.isValidated = null; 
        },
        validateAge() {
            if (this.age) {
                this.isValidated = this.age >= 18;
            }
        }
    }
}


</script>

<style scoped>
.error {
    color: red;
}

.success {
    color: green;
}

li {
    list-style: none;
}
</style>