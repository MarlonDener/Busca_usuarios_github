<template>
    <div id="infomacoes-user">
        <div id="area-infos">
            <div id="area-foto">
                <img :src="avatar">
            </div>
            <div id="area-nome">
                <p>Nome: {{nome}}</p>
                <p class="borda-final">User: {{nomeUser}}</p>
                <p>{{bio}}</p>
                <p>Link: {{link}}</p>
            </div>
        </div>  
    </div>
</template>

<script>
export default {
    props: {
        nome: String,
        nomeUser: String,
        bio: String,
        avatar: String,
        link: String
    },
    data(){
        return{

        }
    }
}
</script>

<style>
    #infomacoes-user{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    #area-infos{
        margin-top: 15px;
        width: 100%;
        display: flex;
        justify-content: space-around;
        flex-direction: column;
        align-items: center;
        padding: 5px;
        box-shadow: 8px 5px 9px 2px rgba(24, 24, 24,0.4);
    }
    #area-foto{
        width: 180px;
        height: 180px;
        border: 1px solid #8D86C9;
        border-radius: 100px;
        margin:9px 0;
    }
    #area-foto img{
        width: 100%;
        height: 100%;
        border-radius: 100px;
    }
    #area-nome{
        width: 100%;
        text-align: center;
    }
    #area-nome p{
        width:100%;
    }
    p{
        color:#fff;
        padding:4px 2%;
    }
    h2{
        font-weight: 300;
        letter-spacing: 2px;
        padding: 5px;
    }
    .borda-final{
        border-bottom: 1px solid rgb(24, 24, 24);
        margin-bottom: 15px;
    }
    .link{
        font-size: 10px;
    }
    small{
        letter-spacing: 2px;
        color: rgb(24, 24, 24);
    }
    @media (max-width:650px){
        #area-foto{
        width: 110px;
        height: 110px;
        border: 1px solid #8D86C9;
        border-radius: 100px;
    }
    }
</style>