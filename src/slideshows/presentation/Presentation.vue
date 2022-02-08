<template lang='pug'>
#Presentation
  .eg-slideshow
    slide
      .tema
        h1 Estudo comparativo entre bibliotecas de testes unitários para uma aplicação Vue.js
      .aluno
        h2 Aluno: Luis Fernando Carvalho Guerreiro da Silva
        h2 Orientador: Prof. Dr. Eduardo da Silva

    slide(:steps=6 enter='swing')
      h1 Problemas

      #problemas
        eg-transition(enter='fadeInLeft')
          p(v-if='step >= 2') Mudanças impactarem negativamente uma aplicação;
        eg-transition(enter='fadeInRight')
          p(v-if='step >= 3') Dificuldade ao trabalhar em um projeto que não tem uma boa cobertura de testes;
        eg-transition(enter='fadeInLeft')
          p(v-if='step >= 4') Usuário final detectar falhas;
        #resultado
          #destaque-1
            eg-transition(enter='slideInLeft')
              p(v-if='step >= 5') = Falta de testes
          #destaque-2
            eg-transition(enter='tada')
              p(v-if='step >= 6') = Baixa Qualidade

    slide
      h1 Therac-25
      h4 Condição de corrida
      <img src="@/therac.png" alt="Therac-25">

    slide
      h1 Y2K-2000
      h4 Datas com apenas 2 dígitos
      <img src="@/y2k.png" alt="Y2K-2000" height="450" width="450">

    slide()
      h1 Testar!

    slide(enter='fadeIn')
      h1 Mas como fazer isso?

    slide(enter='bounceInDown')
      h1 Testes Manuais vs Testes Automáticos

    slide(:steps=3 enter='fadeIn')
      h1 Mas qual ferramenta utilizar?
      #bibliotecas(v-if='step >= 2')
        <img src="@/jest.png" alt="Y2K-2000" height="200" width="200">
        <img src="@/mocha.png" alt="Y2K-2000" height="200" width="200">
</template>

<script>
import eagle from 'eagle.js'
export default {
  mixins: [ eagle.slideshow ],
  infos: {
    // These infos appear on the home page, below the slideshow's thumbnail
    title: 'Presentation',
    description: 'TCC Presentation',
    path: 'presentation'
  }
}
</script>

<style lang='scss'>
@import url(https://fonts.googleapis.com/css?family=Raleway);
#Presentation{
  .eg-slideshow{
    font-family: 'Raleway';
    font-size: 16px;
    background-color: #eef;
    .eg-slide{
      .eg-slide-content{
        height: 100%;
        max-width: 80%;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        .tema,.aluno {
          width: 100%;
        }
        .aluno {
          margin-top: 50px;
        }
        .tema h1 {
          text-align: justify;
        }
        .aluno h2 {
          text-align: end;
          font-size: 1.5rem;
        }
        #problemas p {
          font-size: 3rem;
          margin-bottom: 20px;
        }
        #resultado {
          display: flex;
          justify-content: space-around;
        }
        #destaque-1, #destaque-2 {
          font-weight: bold;
        }
        #destaque-2 {
          color: #FA0D00;
        }
        #bibliotecas {
          display: flex;
          justify-content: space-around;
          margin-top: 50px;
          width: 100%;
        }
      }
    }
  }
}
</style>
