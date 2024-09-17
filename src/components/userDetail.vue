<template>
    <div>
        <h1>User Information</h1>
        <p><strong>Name: </strong> {{ userName }}</p>
        <p><strong>Address:</strong> {{ address }}</p>
        <p><strong>DOB: </strong>{{ dob }}</p>
    </div>
</template>

<script>
export default {
    name:'userDetail',
        data()
        {
            return{
          userName: 'Ashish',
          address: 'Connaught place, New Delhi',
          dob: '18-05-2000'
            }
        }
    }
</script>