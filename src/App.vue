<template>
<h1> Candidate are expected to screenshot this page and post to social Media</h1>
  <h1>I <span> {{ username }} </span>...  Will be attending commuinity development programs</h1>
  <div>
  <div class="imageWrapper" v-if="previewImage.length > 0 ">
  <img class="preview" :src="previewImage" >
  </div>
    <input type="file"  @change="pickFile" accept="image">
  </div>
  <div class="input-down">
    <input class="input-name" type="text"  v-model="username" placeholder="Enter Your Full Name...">

  </div>
</template>
<script>
export default {
   data() {
     return {
     previewImage: "",
     username: ""
    }
  },
  methods: {
  enter() {
    const inputUserName = "" 
    if(inputUserName.value !== "" || inputUserName.value !== null) {
      this.username = inputUserName.value
      // return this.username
    }
    inputUserName.value = ""
  },
  pickFile(e) { 
   let input = e.target
   let file = input.files
   if(file && file[0]) {
    let reader = new FileReader();
    reader.onload = e => { 
      this.previewImage = e.target.result
      
    }
    reader.readAsDataURL(file[0]);

   }
  
  },
 
  },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.imageWrapper img{
  width: 250px;
  height: 250px;
  cursor: pointer;
  background-position: center center;
  margin: 0 auto 30px;
  display: block;
  background-size: cover;
  background: grey;
}
button {
  padding: 12px 15px;
  margin: 20px;
  color: black;
  background: #42b983;
  cursor: pointer;
  border:  none;
  border-radius: 8px;

}
h1{
  font-size:20px ;
}

.input-down{
  margin-top:20px ;
  margin: auto;
}
 .input-name{
  padding: 20px;
  height: 10px;
  width: 300px;
  margin-top:10px;
  border: 1px solid burlywood;
 }
 span {
  color: red;
  font-family: 'Roboto', sans-serif, Arial, Helvetica, sans-serif;

 }
</style>
