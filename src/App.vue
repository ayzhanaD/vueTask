<script>
let id = 0;
    export default{
        data(){
            return{
                myText: '',
                arr:[
                    {id: id++, name: 'name', text: ''},
                    {id: id++, name: 'color', text: ''}
                ]
            }
        },
        methods: {
            addInput(){
                this.arr.push({id: id++, name: this.myText});
                this.myText = '';
            },
            removeInput(data){
                this.arr = this.arr.filter((a) => a !== data);
            },
            saveData(){
                    window.localStorage.setItem('user',  JSON.stringify(this.arr));
            }
        }
    }


</script>

<template>
    <h1>MyForm</h1>
    <div class="container">
        <ul v-for="data in arr" :key="data.id">
            <li><input type="text" v-model="data.name"></li><div class="btn" @click="removeInput(data)">X</div>
        </ul>
        <div class="btn" @click="addInput">+</div>
    </div>
    <div class="inputs">
        <ul v-for="data in arr" :key="data.id">
            <li><h4>{{data.name}} : <input type="text" v-model="data.text"></h4></li> 
        </ul>
    </div>
    <div class="table">
        <h2>Table</h2>
        <ul v-for="data in arr" :key="data.id">
            <li><strong>{{data.name}}: </strong>{{data.text}}</li>
        </ul>
    </div>
    <div class="btn" @click="saveData">save</div>
</template>

<style>
html{
    background: rgb(35, 95, 35);
    font-style: sans-serif;
}
h1{
  color: white;
  text-align: center;
}
h4{
    color: white;
}
ul{
    list-style: none;
}
.btn{
    margin: 20px;
    width: 90px;
    height: 30px;
    border: none;
    border-radius: 10px;
    background: green;
    color: white;
    text-align: center;
    box-shadow: 0 0 5px darkgreen;
}
.btn:hover{
    background: rgb(22, 148, 22);
}
input{
    border: none;
    border-radius: 10px;
    margin: 5px;
    width: 150px;
    height: 30px;
    padding-left: 10px;
    box-shadow: 0 0 5px darkgreen;
}
.table{
    border: 2px solid white;
    color: lightgreen;
    text-align: center;
}
</style>

