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
            <div v-show="showValidationMessage">
                <p v-if="isValidated" class="success">You are ok to use the website</p>
                <p v-else class="error">You are under age</p>
            </div>

        </div>

        <h2>Users List</h2>
        <li v-for="(user, index) in users" :key="index">
            <strong>UserName: </strong> {{ user.Name }}, <strong>Age:</strong> {{ user.Age }} <img :src="user.imageUrl" alt="User Image" width="100px" height="100px"  />
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
            showValidationMessage:false,

            users: [
                { Name: 'rahul', Age: 24, imageUrl: 'https://t3.ftcdn.net/jpg/06/11/89/42/360_F_611894278_6sIqAi9Akdrw9aNulK77WHPJJHJFWTV0.jpg' },
                { Name: 'rohit', Age: 20, imageUrl: 'https://static.vecteezy.com/system/resources/thumbnails/005/346/410/small_2x/close-up-portrait-of-smiling-handsome-young-caucasian-man-face-looking-at-camera-on-isolated-light-gray-studio-background-photo.jpg' }
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
            this.showValidationMessage=false;
        },
        validateAge() {
            if (this.age) {
                this.isValidated = this.age >= 18;
                this.showValidationMessage = true;
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
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.user-item {
    display: flex;
    align-items: center;
}

.user-info {
    display: flex;
    flex-direction: column;
}


</style>