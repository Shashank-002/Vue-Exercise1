<template>
    <div>
        <div class="user-info">
            <h1>User Information</h1>
            <p><strong>Name: </strong> {{ userName }}</p>
            <p><strong>Address:</strong> {{ address }}</p>
            <p><strong>DOB: </strong>{{ dob }}</p>
        </div>

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
            <img :src="user.imageUrl" alt="User Image" /><br>
            <strong>UserName: </strong> {{ user.Name }} <br>
            <strong>Age:</strong> {{ user.Age }}
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
            showValidationMessage: false,

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
            this.showValidationMessage = false;
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
h1 {
    font-size: 28px;
    color: #333;
    margin-bottom: 20px;
    font-weight: bold;
    text-align: center;
    text-transform: uppercase;
    letter-spacing: 2px;
}

h2 {
    font-size: 28px;
    color: #333;
    margin-bottom: 20px;
    font-weight: bold;
    text-align: center;
    text-transform: uppercase;
    letter-spacing: 2px;
}

p {
    font-size: 16px;
    color: #555;
    line-height: 1.6;
    margin-bottom: 15px;
}

p strong {
    color: #333;
    font-weight: bold;
}


p:last-child {
    margin-bottom: 0;
}

.user-info {
    max-width: 600px;
    margin: 10px auto;
    padding: 20px;
    border-radius: 10px;
    background-color: #f9f9f9;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}


button {
    padding: 10px 20px;
    background: linear-gradient(135deg, #1e90ff, #007bff);
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 14px;
    margin: 5px 0;
    font-weight: 400;
    cursor: pointer;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
}

button:hover {
    background: linear-gradient(135deg, #007bff, #0056b3);
    box-shadow: 0 6px 10px rgba
}

.error {
    color: red;
}

.success {
    color: green;
}

li {
    list-style: none;
    margin-bottom: 30px;
}

li img {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin-bottom: 10px;
}
</style>