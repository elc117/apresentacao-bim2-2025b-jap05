# apresentacao-bim2-2025b-jap05

# Primeira Etapa
 #### O primeiro passo para solucionar o problema foi entender o código, logo de cara foi possível ver que se tratava de um programa de operações financeiras que atualizariam a variavel saldo. Portando, lendo as declarações do código os valores esperados seriam:
##
- Saldo Inicial: 0
- Saldo Final: 10000
- Valor de Depósito: 10
- Valor de Saque: 5
#
Nessa etapa do código tudo parecia normal, até a hora de executar, foi ai que percebi que o resultado final não condizia com o esperado, sempre resultando em um valor menor que 10.000.

![Desktop 2025 11 18 - 01](https://github.com/user-attachments/assets/4f21a35d-ef92-4c27-bd7f-1f3cc360d33c)


Voltando a análise do código, as funções responsáveis por manipular o valor do saldo são 

<img width="370" height="188" alt="image" src="https://github.com/user-attachments/assets/800bf62b-f47d-4576-966c-e162f1bd48e5" />


O problemas que eu percebi é que ambas estão sendo compartilhadas pelas threads
<img width="722" height="233" alt="image" src="https://github.com/user-attachments/assets/f680ae30-6462-4753-9f70-be7304f45760" />


Essas threads estão rodando ao mesmo tempo e entrando em conflito, enquanto uma tenta alterar o valor do saldo, a outra interrompe o processo e usa como base o valor do saldo desatualizado
####
Para corrigir isso, a exercício sugere usar a palavra chave synchronized pra fazer um exclusão mútua dos métodos afetados, nesse caso seriam as funções que modificam a varial que está sendo compartilhada, o saldo.
<img width="503" height="186" alt="image" src="https://github.com/user-attachments/assets/e47cfa9e-958a-40fc-b030-5120b3a8f3a2" />

Com essa alteração as threads param de se interromper e o programa executa da forma esperada

![Desktop 2025 11 18 - 01 (2)](https://github.com/user-attachments/assets/992ac0eb-3690-45bf-aa88-5743474a6386)

#### Considerações Finais
Indenficar as variáveis, e seus valores esperados foi de longe a parte mais fácil da atividade, afinal todas foram explicitamente declaradas. A principal dificuldade foi entender o problema era a condição de corrida das threads, isso que causava a perda de informação e consequentemente resultava em valores menores do que o esperado, mas como a própria atividade já sujeria a forma de concertar esse erro, só bastava compreender o local apropriado pra utilizar o synchronized
