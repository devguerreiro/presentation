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

    slide(enter='fadeIn')
      h1 Como resolver e/ou evitar?

    slide()
      h1 Testando!

    slide(enter='fadeIn')
      h1 Mas como fazer isso?

    slide(enter='bounceInDown')
      h1 Testes Manuais vs Testes Automáticos

    slide(enter='fadeIn')
      h1 Mas qual ferramenta utilizar?

    slide.comparacao(enter='fadeIn')
      <img id="jest" src="@/jest.png" alt="Y2K-2000" height="450" width="450">
      <img id="mocha" src="@/mocha.png" alt="Y2K-2000" height="450" width="450">

    slide(:steps=5 enter='fadeIn')
      h1 Critérios de Avaliação
      .criterios
        ol
          li(v-if='step >= 2') Configuração Inicial
          li(v-if='step >= 3') Sintaxe ou Legibilidade
          li(v-if='step >= 4') Desempenho
          li(v-if='step >= 5') Curva de Aprendizado
    slide(:steps=13 enter="fadeIn")
      h1 Configuração Inicial
      h2(v-if='step >= 1 && step <= 3') Instalação
      .instalacao
        eg-transition(enter='fadeIn')
          eg-code-block(lang='bash' v-if='step >= 2 && step < 4') $ yarn add --dev jest
        eg-transition(enter='fadeIn' )
          eg-code-block(lang='bash' v-if='step >= 3 && step < 4') $ yarn add --dev mocha
      h2(v-if='step >= 4') Escrita dos Testes
      .classe
        eg-transition(enter='fadeIn')
          eg-code-block(v-if='step === 4' lang='javascript').
            class Pessoa {
              MAIORIDADE = 18

              constructor(nome, idade) {
                this.nome = nome
                this.idade = idade
              }

              ehAdulta() {
                return this.idade >= this.MAIORIDADE
              }
            }

            module.exports = Pessoa;
        eg-transition(enter='fadeIn')
          eg-code-block(v-if='step >= 5' lang='javascript').
            const assert = require("assert")
            const Pessoa = require("../Pessoa")

            describe("Classe Pessoa", () => {
              it('deve retornar verdadeiro se uma pessoa for maior de idade', () => {
                const Fulano = new Pessoa("Fulano", 19)

                assert.equal(Fulano.ehAdulta(), true)
              });
            }

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
      .eg-slide-content {
        height: 100%;
        max-width: 80%;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        p {
          font-size: 3rem;
          margin-bottom: 20px;
        }
      }
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
      .criterios {
        width: 100%;
        li {
          font-size: 3rem;
        }
      }
      .instalacao {
        margin-top: 50px;
        .eg-code-block {
          margin-bottom: 50px;
          border: 2px solid black;
          border-radius: 10px;
          box-shadow: 5px 5px 10px;
          font-size: 2rem;
        }
      }
      .classe {
        margin-top: 50px;
        .eg-code-block {
          border: 2px solid black;
          border-radius: 10px;
          box-shadow: 5px 5px 10px;
          font-size: 2rem;
        }
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
    }
    .comparacao {
      background: url("../../duelo2.jpg");
      background-size: 100% 100%;
      background-repeat: no-repeat;
      .eg-slide-content {
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
      }
      #jest {
        transform: translate(-90px, 30px) rotateY(25deg)
      }
      #mocha {
        transform: translateX(80px) rotateY(-30deg)
      }
    }
  }
}
</style>
