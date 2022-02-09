<template lang='pug'>
#Presentation
  .eg-slideshow
    slide
      .tema
        h1 Estudo comparativo entre bibliotecas de testes unitários para uma aplicação Vue.js
      .aluno
        h2 Aluno: Luis Fernando Carvalho Guerreiro da Silva
        h2 Orientador: Prof. Dr. Eduardo da Silva

    slide(:steps=6 enter='bounceIn')
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
              p(v-if='step >= 5') = Ausência de testes
          #destaque-2
            eg-transition(enter='tada')
              p(v-if='step >= 6') = Baixa Qualidade

    slide(enter='fadeIn')
      h1 Therac-25
      h4 Condição de corrida
      <img src="@/therac.png" alt="Therac-25">

    slide(enter='fadeIn')
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
      h1 E qual ferramenta utilizar?

    slide.comparacao(enter='fadeIn')
      <img id="jest" src="@/jest.png" alt="Jest Logo" height="450" width="450">
      <img id="mocha" src="@/mocha.png" alt="Mocha Logo" height="450" width="450">

    slide(:steps=5 enter='fadeIn')
      h1 Critérios de Avaliação
      .criterios
        ol
          eg-transition(enter='fadeIn')
            li(v-if='step >= 2') Configuração Inicial
          eg-transition(enter='fadeIn')
            li(v-if='step >= 3') Sintaxe ou Legibilidade
          eg-transition(enter='fadeIn')
            li(v-if='step >= 4') Desempenho
          eg-transition(enter='fadeIn')
            li(v-if='step >= 5') Curva de Aprendizado
    slide(:steps=3 enter='fadeIn')
      h1 Configuração Inicial
      h2 Instalação
      .instalacao
        eg-transition(enter='fadeIn')
          eg-code-block(lang='bash' v-if='step >= 2') $ yarn add --dev jest
        eg-transition(enter='fadeIn' )
          eg-code-block(lang='bash' v-if='step >= 3') $ yarn add --dev mocha
    slide(enter='fadeIn')
      h1 Configuração Inicial
      h2 Escrita dos Testes
      .classe
        eg-transition(enter='fadeIn')
          eg-code-block(lang='javascript').
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
    slide(:steps=6 enter='fadeIn')
      h1 Configuração Inicial
      h2 Escrita dos Testes
      .teste-mocha
        eg-transition(enter='fadeIn')
          img(src="@/mocha.png" alt="Mocha Logo" height="150" width="150")
        eg-transition(enter='fadeIn')
          eg-code-block(lang='javascript').
            const assert = require("assert") <eg-code-comment :active='step === 2 && true' enter='flipInY'> Importa asserção do Node.js</eg-code-comment>
            const Pessoa = require("../Pessoa") <eg-code-comment :active='step === 3 && true' enter='flipInY'> Importa a classe Pessoa</eg-code-comment>

            describe("Classe Pessoa", () => { <eg-code-comment :active='step === 4' enter='flipInY'> Define o escopo do teste</eg-code-comment>
              it('deve retornar verdadeiro se uma pessoa for maior de idade', () => { <eg-code-comment :active='step === 5' enter='flipInY'> Descreve o teste</eg-code-comment>
                const Fulano = new Pessoa("Fulano", 19)

                assert.equal(Fulano.ehAdulta(), true) <eg-code-comment :active='step === 6' enter='flipInY'> Valida o retorno</eg-code-comment>
              });
            }
    slide(:steps=3 enter='fadeIn')
      h1 Configuração Inicial
      h2 Escrita dos Testes
      .teste-jest
        eg-transition(enter='fadeIn')
          img(src="@/jest.png" alt="Jest Logo" height="150" width="150")
        eg-transition(enter='fadeIn')
          eg-code-block(lang='javascript').
            const Pessoa = require("./Pessoa") <eg-code-comment :active='step === 2' enter='flipInY'> Importa somente a classe</eg-code-comment>

            describe("Classe Pessoa", () => {
              it('deve retornar verdadeiro se uma pessoa for maior de idade', () => {
                const Fulano = new Pessoa("Fulano", 19)

                expect(Fulano.ehAdulta()).toBe(true) <eg-code-comment :active='step === 3' enter='flipInY'> Asserção integrada</eg-code-comment>
              });
            }
    slide(enter='fadeIn')
      h1 Configuração Inicial
      h2 Reconhecimento dos testes
      .dirs
        #jest
          eg-transition(enter='fadeIn')
            img(src="@/dir-jest.png" alt="Jest Logo" height="400" width="700")
          p Jest
        #mocha
          eg-transition(enter='fadeIn')
            img(src="@/dir-mocha.png" alt="Jest Logo" height="400" width="700")
          p Mocha
    slide(:steps='3' enter='fadeIn')
      h1 Sintaxe ou Legibilidade
      .sintaxe
        #mocha
          img(src="@/mocha.png" alt="Mocha Logo" height="150" width="150")
          eg-transition(enter='fadeIn')
            eg-code-block(lang='javascript').
              it('deve retornar verdadeiro se uma pessoa for maior de idade', () => { <eg-code-comment :active='step === 5' enter='flipInY'> Descreve o teste</eg-code-comment>
                const Fulano = new Pessoa("Fulano", 19)

                assert.equal(Fulano.ehAdulta(), true) <eg-code-comment :active='step === 2' enter='flipInY'> Leitura mais técnica</eg-code-comment>
              });
        #jest
          img(src="@/jest.png" alt="Jest Logo" height="150" width="150")
          eg-transition(enter='fadeIn')
            eg-code-block(lang='javascript').
              it('deve retornar verdadeiro se uma pessoa for maior de idade', () => {
                const Fulano = new Pessoa("Fulano", 19)

                expect(Fulano.ehAdulta()).toBe(true) <eg-code-comment :active='step === 3' enter='flipInY'> Leitura mais natural</eg-code-comment>
              });
    slide(:steps='6' enter='fadeIn')
      h1 Desempenho
      .desempenho
        .airbnb(v-if='step === 1')
          img(src='@/airbnb.png' width='350')
          p Gary Borton
        ul
          eg-transition(enter='fadeIn')
            li(v-if='step >= 2 && step < 5') Paralelização
          eg-transition(enter='fadeIn')
            li(v-if='step >= 3 && step < 5') Round Robin
          eg-transition(enter='fadeIn')
            li(v-if='step >= 4 && step < 5') Cache
        eg-transition(enter='fadeIn')
          table(v-if='step >= 5')
            thead
              tr
                th Execução
                th Resultado Mocha (s)
                th Resulta Jest (s)
            tbody
              tr
                td 1
                td 0.3
                td 0.194
              tr
                td 2
                td 0.2
                td 0.178
              tr
                td 3
                td 0.3
                td 0.221
              tr
                td 4
                td 0.3
                td 0.167
              tr
                td 5
                td 0.3
                td 0.177
              eg-transition(enter='bounceIn')
                tr(v-if='step === 6').bold
                  td Média
                  td 0.28
                  td 0.187
    slide
      h1 Curva de Aprendizado
      .curva
        img(src='@/graph.png' alt="Gráfico Pesquisa" height='500')
        p Satisfação: usariam novamente / (usariam novamente + não usariam novamente)
    slide
      h1 Conclusão
      .conclusao
        eg-transition(enter='fadeIn')
          table
            thead
              tr
                th Critério
                th Mocha
                th Jest
            tbody
              tr
                td Configuração Inicial
                td A configuração inicial é simples em aplicações pouco complexas. Em aplicações mais complexas é necessário adicionar funcionalidades através de outras bibliotecas
                td A configuração inicial é simples mesmo em aplicações mais complexas
              tr
                td Sintaxe/Legibilidade
                td Dependendo da biblioteca utilizada em conjunto, a sintaxe/legibilidade pode não ser muito compreensível
                td As APIs integradas são de fácil compreensão pois permitem uma leitura mais natural
              tr
                td Desempenho
                td Possui desempenho inferior por executar por padrão em modo serial
                td Possui melhor desempenho devido à paralelização, por utilizar round robin e fazer uso de cache com babel
              tr
                td Aprendizado
                td Por possuir diversas bibliotecas compatíveis, é possível que se trabalhe em uma aplicação que utilize uma biblioteca da qual não possui conhecimento, sendo necessário aprender a utilizá-la
                td Tem a maior parte da comunidade utilizando e satisfeitos. Quem domina Jest consegue trabalhar em qualquer aplicação que utilize Jest
    slide
      h1 Dúvidas?
      .duvidas
        img(src='@/confused.gif' width='700px')
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
    img {
      max-width: 100%;
    }
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
      .bold {
        font-weight: bold;
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
          margin-top: 50px;
        }
      }
      .eg-code-block {
        border: 2px solid black;
        border-radius: 10px;
        box-shadow: 5px 5px 10px;
        font-size: 2rem;
      }
      .instalacao, .classe, .teste-mocha, .teste-jest {
        margin-top: 50px;
        .eg-code-block {
          margin-bottom: 50px;
        }
      }
      .teste-mocha, .teste-jest {
        position: relative;
        img {
          position: absolute;
          top: -125px;
          right: -50px;
          z-index: 2;
        }
        .eg-code-block {
          font-size: 1.8rem;
        }
      }
      .dirs {
        width: 100%;
        margin-top: 50px;
        display: flex;
        justify-content: space-around;
        #jest, #mocha {
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          p {
            font-size: 2rem;
          }
        }
      }
      .sintaxe {
        margin-top: 50px;
        #jest {
          margin-top: 100px;
        }
        #jest, #mocha {
          position: relative;
          img {
            position: absolute;
            top: -125px;
            right: -50px;
            z-index: 2;
          }
        }
      }
      .desempenho {
        width: 100%;
        font-size: 3rem;
        margin-top: 50px;
        .airbnb {
          display: flex;
          flex-direction: column;
          align-items: center;
        }
        table, th, td {
          border: 1px solid black;
          padding: 10px;
        }
        table {
          margin: 0 auto;
        }
        li {
          margin-top: 25px;
        }
      }
      .curva {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 0 auto;
        margin-top: 50px;
        p {
          font-size: 2rem;
          margin-top: 10px;
        }
      }
      .conclusao {
        margin-top: 50px;
        font-size: 1.75rem;
        table, th, td {
          border: 1px solid black;
          padding: 10px;
        }
      }
      .duvidas {
        margin-top: 50px;
        width: 100%;
        display: flex;
        justify-content: center;
        img {
          width: 700px;
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
