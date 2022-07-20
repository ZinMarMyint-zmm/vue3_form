<template>
  <form @submit.prevent="onSubmit">
    <label for="">Email</label>
    <input type="email" v-model="email" required>

    <label for="">Password</label>
    <input type="password" v-model="password">
    <p v-if="errorMsg" class="error">{{errorMsg}}</p>

    <label for="">Roles</label>
    <select v-model="role">
        <option value="developer">Web developer</option>
        <option value="designer">Web designer</option>
    </select>

    <div>
        <label for="">Skills</label>
        <input type="text" @keyup="addSkill" v-model="skill">
    </div>
    <div v-for="skill in skills" :key="skill">
        <p>{{skill}} 
            <span class="cross" @click="deleteSkill(skill)">&#x2716;</span>
        </p>
    </div>

 
<!-- single checkbox -->
    <input type="checkbox" v-model="accept">
    <label for="">Accept Terms and conditions</label>

    <div class="align">
        <button class="create">
            create account
        </button>
    </div>

<!-- mutiple checkbox -->
    <!-- <label for="">check names</label>
    <div>
        <input type="checkbox" value="zinmarmyint" v-model="names">
        <label for="">zin mar myint</label>
    </div>
    <div>
        <input type="checkbox" value="maymi" v-model="names">
        <label for="">may mi</label>
    </div>
    <div>
        <input type="checkbox" value="zmmt" v-model="names">
        <label for="">zin may mi tun</label>
    </div>
    <div>
        <input type="checkbox" value="zmm" v-model="names">
        <label for="">zin may mi</label>
    </div> -->
  </form>
  <p>email- {{email}}</p>
  <p>password- {{password}}</p>
  <p>role- {{role}}</p>
  <p>accept- {{accept}}</p>
  <!-- <p>names: {{names}}</p> -->
</template>

<script>
export default {
    data(){
        return{
            email:"zmm@gmail.com",
            password:"",
            role:"",
            accept:false,
            skills:[],
            skill:"",
            errorMsg:""
            // names:[]
        }
    },
    methods:{
        addSkill(e){
            if(e.keyCode===13 && this.skill){
                
                this.skills.push(this.skill);
                this.skill=""
            }
            
        },
        deleteSkill(skill){
            this.skills=this.skills.filter(el=>{
                let empty = (el != skill);
                
                return empty;
            })
            
        },
        onSubmit(){
            if(this.password.length<8){
                this.errorMsg="Password must be at least 8 characters."
            }
        }
    }
}
</script>

<style>
form{
    max-width: 420px;
    background: white;
    margin: 30px auto;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label{
    color:#7a7979;
    display: inline-block;
    margin:25px 0 15px;
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input,select{
    display: block;
    border: none;
    border-bottom: 1px solid #ddd;
    width: 100%;
    box-sizing: border-box;
    color:#555;
    padding:10px 5px;
}
input[type="checkbox"] {
    display: inline-block;
    width:16px;
    margin: 0 10px 0 0;
    position: relative;
    top:2px;
}
.cross{
    cursor: pointer;
    color:#db4e4e;
}
.create{
    background-color:royalblue;
    font-size: 0.7rem;
    font-weight: bold;
    text-transform: uppercase;
    color:white;
    padding:10px;
    border-radius:10px;
    border:none;
    margin:20px auto;
    
}
.create:hover{
    background: #6080e0;
}
.create:active{
    background-color:#375ac3;
}
.align{
    text-align: center;
}
.error{
    color:#db4e4e;
}
</style>