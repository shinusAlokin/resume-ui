<template>
        <!-- <SearchBar  v-model="search" placeholder="search by name"/> -->
        <input type="text" v-model="search">
        <p>search is: {{ search }}</p>
        <div class="listing-heading">
            <ul class="heading-list">
                <li  v-for="item in heading" :key="item.id">{{ item.text }}</li>
            </ul>
        </div>
        <!-- <button @click="getContent()">Load</button> -->
        
        <span class="looper-span" v-for="item in content">
        <div class="listing-content" v-for="v in item" >
            <ul class="content-list">
                    <li class="list name-list">{{v.name}}</li>
                    <li class="list email-list">{{v.email_address}}</li>
                    <li class="list phone-list">{{v.phone_number}}</li>
                    <li class="list date-list">{{v.date_applied}}</li>
                    <span class="icon-span">
                        <i @click="showHidden" class="fa-solid fa-ellipsis-vertical"></i>
                        <!-- <div class="main-hidden-container">
                            <div class="hidden-content" :class="[hiddenKebab ? 'active': '']">
                                <div class="content edit-list">
                                    <div><a href="">Edit</a></div>
                                    <div><a href="">Delete</a></div>
                                </div>
                            </div>
                        </div> -->
                        <!-- <div class="accordian">
                            <div class="container" :class="[hiddenKebab ? 'active': '']">
                                <div class="content">
                                    <div class="edit"><a href="">Edit</a></div>
                                    <div class="delt"><a href="">Delete</a></div>
                                </div>
                            </div>
                         </div> -->
                    </span>                   
            </ul>
        </div>
    </span>
       
</template>

<script>
import axios from 'axios'
import SearchBar from "./SearchBar.vue"


export default{

    name: "Listing",
    components:{
        SearchBar,
    },
    data(){
        return{
            heading:[
                {id:1, text: 'Name'},
                {id:2, text: 'Email'},
                {id:3, text: 'Phone'},
                {id:4, text: 'Applied On'}
            ],
            content:[],
            hiddenKebab: false,
            search:''
        }
    },
    methods:{
       async getContent(){
           await axios.get(`http://127.0.0.1:8000/get_basic/`, {
            headers:{
                    'content-type':'application/json',
                    'Accept':'application/json'
                }
            }).then((response) =>{
                this.content = response.data
                console.log(response.data)
            }).catch((error) => {
                console.log(error)
            })
    },
    },
    created(){
        this.getContent()
        console.log(this.content)
    },
    computed:{
        filteredPost(){
             return this.content.filter(cont => cont.name == this.search)
        }
    },
}
</script>

<style scoped>

   ul{
        display: flex;
        list-style: none;
        justify-content:space-between;
        align-items: center;
        text-align: left;
        position: relative;
        padding: 1em;
        /* padding-right: 1em; */
        flex-basis: 10%;
    }

    li{
        font-size: 0.9rem;
        line-height: 30px;
        padding: 0 0.9em;
        width: 24%;
    }

    ul i{
        cursor: pointer;
        position: absolute;
        top: 0;
        left: 0;

    }

    .name-list{
        margin-left: 10px;
    }

    .icon-span{
        position: absolute;
        left: 99%;
    }

    
    .listing-heading{
        margin-top: 20px;
        text-align: center;
        width: 100%;
        padding-top: 0.2em;
        background-color: rgba(0, 128, 128, 0.2);
        box-shadow: 2px 2px 5px rgba(154, 150, 150, 0.2);
    }

    .listing-heading > ul:first-child{
        margin-left: 5px;
    }

    .listing-content{
        width: 100%;
        margin-top: 0;
        box-shadow: 2px 2px 5px rgba(154, 150, 150, 0.2);
        border-bottom: 1px solid rgb(114, 110, 110, 0.1);
    }

    .listing-content ul{
        padding-top: 1em;
    }

    .looper-span{
        width: 100%;
        margin: 0;
    }


</style>