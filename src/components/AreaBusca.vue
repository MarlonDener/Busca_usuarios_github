<template>
 <div class="application">
    <div id="area-busca" v-if="buscaAtiva">
        <div>
            <input type="text" id="buscar-usuario" placeholder="Digite o user" @keypress.enter="buscar">
            <button id="btn-buscar" @click="buscar">Buscar</button>          
        </div>    
    </div>
    <div id="infos" v-if="infosUsuario">
            <Infos :nome="nome" :link="link" :nomeUser="nomeUser" :bio="bio" :avatar="avatar" :buscaAtiva="buscaAtiva" />
            <div id="area-btb-voltar">
                <button id="btn-voltar" @click="voltar">Voltar</button>   
            </div> 
    </div>
</div>
</template>

<script>
import Infos from './AreaInfos.vue'
import axios from 'axios'
export default {
    components: {Infos},
    data(){
        return{
            buscaAtiva: true,
            infosUsuario: false,
            axios: axios,
            avatar: '',
            nome: '',
            nomeUser: '',
            bio: '',
            link: '',
        }
    },
    methods: {
        buscar(){
            let capturarUser = document.querySelector('#buscar-usuario').value

            if(capturarUser == ''){
                alert('Digite o campo corretamente!')
            }else{
            this.buscaAtiva = false 
            this.infosUsuario = true                
                const url = `https://api.github.com/users/${capturarUser}`
                this.axios.get(url).then((response) =>{
                    console.log(response.data);
                    this.avatar = response.data.avatar_url
                    this.nome = response.data.name
                    this.nomeUser = response.data.login
                    this.bio = response.data.bio
                    this.dt = response.data.created_at
                    this.link = response.data.html_url
                })                
            }
        },
        voltar(){
            this.buscaAtiva = true,
            this.infosUsuario = false
        }
    }
}
</script>

<style>
    .application{
        width:100%;
        height: 100%;
        display:flex;
        align-items: center;
        justify-content: center;
    }
    #area-busca{
        background-color: #2729326c;
        border-radius: 20px;
        width: 50%;
        height: 50%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    #buscar-usuario{
        border: none;
        height: 40px;
        width: 270px;
        padding: 10px;
        border-radius: 2px;
        outline: none;
        font-weight: bold;
        font-size: 15px;
    }

    #btn-buscar, #btn-voltar{
        height: 40px;
        width: 100px;
        border: none;
        color:#ccc;
        background-color: #2314af;
        box-shadow: 2px 2px 2px rgb(13, 1, 80);
        letter-spacing: 2px;
        font-weight: bold;
        margin:0 5px;
        cursor:pointer;
        outline: none;
        border-radius: 2px;
        transition:0.4s linear;
    }
    #btn-buscar:hover, #btn-voltar:hover{
         border: none;
         filter:brightness(1.5);
    }
    #infos{
        width: 100%;

    }
    #area-btb-voltar{
        display: flex;
        justify-content: center;
    }

    @media (max-width:800px){
        #buscar-usuario{
            width:90%;
            display: inline-block;
        }
         #area-busca{
            text-align: center;
            width:80%;
          }

          #btn-buscar, #btn-voltar{
              width:120px;
              margin-top: 10px;
          }
        
    }
</style>