---
title: "Automação de Sistemas"
date: 2023-01-11T10:15:08-03:00
thumbnail:
  src: "/post/automacao_sistemas/automacao_sistemas.jpg"
categories:
  - "Automação"
tags:
  - "Automação"
  - "Robótica"
  - "Indústria"
  - "Máquinas"
  - "Redes"
draft: true
---

Anotações do curso de **Automação de Sistemas** e abrange áreas de automação, projeto, robótica, indústria, máquinas e redes.
<!--more-->
Este curso é oferecido pelo [Instuto Federal do Rio Grande do Sul (IFRS)](https://moodle.ifrs.edu.br/) e utiliza como base o material **Automação de Sistemas**, produzido pelos professores Fernando, Moacir e Renato, para a Rede e-Tec Brasil.

# 1 - Automação e Projeto

## 1.1 - Automação de sistemas	

### Automação
Pode se definir automação como a tecnologia que se ocupa da utilização de sistemas mecânicos, eletroeletrônicos e computacionais na operação e controle da produção.

### Automação ou mecanização
A mecanização consiste simplesmente no uso de máquinas para realizar um trabalho, substituindo o esforço físico do homem. Já a automação possibilita fazer um trabalho por meio de máquinas controladas automaticamente, capazes de se autorregularem.

### Desenvolvimento da automação
A automação só ganhou destaque na sociedade quando o sistema de produção agrário e artesanal transformou-se em industrial, a partir da segunda metade do século XVIII, inicialmente na Inglaterra.
Por volta de 1788, James Watt desenvolveu um mecanismo de regulagem do fluxo de vapor em máquinas. Isto pode ser considerado um dos primeiros sistemas de controle com realimentação.

![Vapor](../automacao_sistemas/centrifugal_governor.jpg)

*Fonte: [Wikipedia](https://en.wikipedia.org/wiki/Centrifugal_governor)*

### Classificação dos sistemas automatizados
A automação industrial pode ser desdobrada em:
- Automação de planejamento;
- Automação de projeto;
- Automação de produção.

No universo dos sistemas automatizados, o interesse recai especialmente no Sistemas Industriais de Produção Automatizados.
- Automação fixa;
- Automação programável;
- Automação flexível.

#### Automação fixa
Baseada em uma linha de produção especialmente projetada para a fabricação de um produto específico e determinado. É utilizada quando o volume de produção dever ser muito elevado.
O equipamento é, em geral, de custo elevado, porém devido a sua alta taxa de produção, o custo fixo é dividido numa grande quantidade de unidades fabricadas.
O risco que se enfrenta com a automação fixa é que qualquer alteração nas vendas ou alteração do produto poderá tornar a linha obsoleta, trazendo um grande prejuízo.

#### Automação programável
Baseada em um equipamento com capacidade de fabricar uma variedade de produtos com características diferentes, segundo um programa de instruções previamente introduzido. Esse tipo de automação é utilizado quando o volume de produção de cada item é baixo.
Um sistema típico de automação programável são as máquinas de usinagem com controle Código Numérico Computadorizado (CNC).
Em termos de economia, o custo do equipamento pode ser diluído num grande número de produtos, mesmo que estes tenham diferentes configurações.

#### Automação flexível
Pode ser entendida como uma solução de compromisso entre a automação fixa e a automação programável. Também é conhecida como sistema de Manufatura Integrada por Computador (CIM) e, em geral, parece ser mais indicado para o volume médio de produção.
O equipamento deve ser programado para produzir uma variedade de produtos com algumas características ou configurações diferentes, mas a variedade dessas características é normalmente mais limitada do que aquela permitida pela automação programável.
Os sistemas flexíveis automatizados consistem, em geral, de estações de trabalho autônomas com um alto grau de integração. Essas estações estão interligadas por um sistema de manuseio, transporte e armazenamento do material. Um computador central é utilizado para controlar e monitorar as diversas atividades que ocorrem no sistema, determinando a rota das diversas partes para as estações apropriadas, controlando as operações previamente programadas nas diferentes estações.

### O impacto da automação na sociedade
A automação geralmente reduz custos e aumenta a produtividade do trabalho. A automação pode livrar os trabalhadores de atividades monótonas, repetitivas ou mesmo perigosas.
Apesar dos benefícios, o aumento da automação vem causando também alguns problemas para os trabalhadores:
- Aumento do nível de desemprego, principalmente nas áreas em que atuam profissionais de baixo nível de qualificação;
- A experiência de um trabalhador se torna rapidamente obsoleta;
- Muitos empregos que eram importantes estão se extinguindo, como telefonistas, atualmente perfeitamente substituíveis por centrais de telefonia automáticas.

## 1.2 - Projeto de sistemas de automação

### O projeto
Para garantir os melhores resultados possíveis, tanto a curto quanto a longo prazo, um projeto de automação industrial deve:
- Ser desenvolvido sistematicamente – ou seja, deve ser desenvolvido seguindo um padrão lógico que permita o seu desenvolvimento passo a passo;
- Ser bem estruturado – ter uma organização que permita compreender o projeto facilmente; e
- Dispor de documentação detalhada – todos os passos e informações necessárias para a montagem e manutenção dos sistemas devem estar disponíveis.

### Modelo de fases para a elaboração de projetos
Todos os projetos técnicos e compõe-se das seguintes fases:
- Especificação;
- Projeto;
- Implementação;
- Integração e instalação.

#### Fase 1 – Especificação
Fase de formalização da tarefa, onde ela é descrita de forma precisa e detalhada.

Ao final dessa etapa teríamos:
- Descrição verbal do sistema;
- Croqui e/ou layout do sistema; e 
- Estrutura básica do sistema de controle.

#### Fase 2 – Projeto
Sua descrição deve apresentar graficamente a função e o comportamento do controle, de acordo com o processo, independentemente da tecnologia.

Ao final dessa etapa teríamos:
- Representações do funcionamento do sistema, tais como diagramas trajeto-passo;
- Tabela verdade;
- Definição dos módulos do programa com os seus respectivos fluxogramas ou flow chart;
- Diagramas de circuitos elétricos de comando, de potência e também diagramas pneumáticos ou hidráulicos, quando necessário; e
- Listas de componentes.

#### Fase 3 – Implementação
É a conversão da solução encontrada em um projeto detalhado e o desenvolvimento do programa de controle.
No caso de um sistema com o controle por CLP, seria gerado o programa em uma das linguagens definidas na norma IED 61132-3: Linguagem sequencial, diagrama de funções, diagrama ladder, linguagem estruturada ou lista de instruções.

#### Fase 4 – Instalação e testes
Nessa fase são construídas as instalações, carregado o programa de controle e, após, testada a atuação conjunta do sistema de automação e da instalação conectada.

#### Documentação
Trata-se de um requisito necessário para que uma instalação possa ser mantida e ampliada.

A documentação compõe-se de referências sobre cada fase do projeto, impressão dos programas de controle e, eventualmente, também outras descrições sobre este programa. 
- Memorial descritivo;
- Croquis e layouts da planta;
- Diagramas de circuitos elétricos de comando e de potência (unifilar ou multifilar);
- Diagramas de circuitos pneumáticos e hidráulicos. Desenhos técnicos de detalhamento dos componentes;
- Esquemas de conexão de bornes;
- Impressão dos programas de controle;
- Listas de alocação de entradas e saídas (fazendo parte da impressão do programa de controle);
- Listas de materiais; e
- Outros documentos que se fizerem necessários.

# 2 - Robótica e Indústria

## 2.1 - Robótica industrial
A palavra robô tem a origem atribuída ao escritor tcheco Karel Capek, o qual utilizou em seus livros o termo tcheco robota (que significa trabalhador escravo). Esse termo, traduzido para o inglês tornou-se robot, e teve o seu uso popularizado pelo escritor Issac Asimov com seu livro “Eu, Robô”, de 1950, data em que pela primeira vez foi utilizado o termo robótica para denominar ciência que estuda os sistemas robóticos. Este interesse gerou no passado vários sistemas que tentavam automatizar movimentos, mas que dificilmente passavam de sistemas mecânicos com programação fixa.

A primeira patente de um dispositivo robótico foi feita por um britânico, Cyril W. Kenward, em 1954. Porém, o conceito moderno de robô industrial foi criado por Joseph Engelberger, que, em conjunto com o americano George C. Devol, desenvolveu o primeiro protótipo comercial chamado Unimate. A primeira instalação industrial foi realizada pela Ford Motor Company, que utilizou um modelo Unimate para realizar o descarregamento robotizado de uma máquina de fundição sob pressão.

Em 1974 a mesma empresa que criou o Unimate lançou um novo robô de 6 eixos chamado PUMA, o qual foi responsável pela popularização deste tipo de equipamento. Ainda existem muitos desses modelos em atividade até os dias de hoje. PUMA são as iniciais de Programmable Universal Machine for Assembly, ou seja, máquina universal programável para montagem.

Os sistemas de controle dos robôs normalmente estão localizados externamente à parte mecânica do mesmo, normalmente em um gabinete metálico, o qual chamamos controlador. Esse gabinete normalmente é conectado por cabos ao atuador, podendo portanto localizar-se a uma distância segura da área de trabalho. Para completar o sistema ainda temos que contar com uma fonte de alimentação de alta potência para o acionamento dos eixos (normalmente localizada no mesmo gabinete do controlador) e da interface de programação do robô.

## 2.2 - Robôs industriais manipuladores


# 3 - Máquinas e Redes

## 3.1 - Controle numérico computadorizado – CNC

### Histórico
O comando numérico computadorizado fornece uma série de vantagens quando comparado aos métodos de usinagem convencionais. Além da economia no processo de usinagem, podem-se citar:
1. Aumento na produtividade;
2. Facilidade de programação e controle de produção;
3. Troca automática de velocidades;
4. Redução de custos em controle de qualidade, aumento da qualidade;
5. Padronização de ferramentas, ferramentas intercambiáveis;
6. Alta versatilidade de operações;
7. Aumento do controle em operações complexas;
8. Possibilidade de simulações de usinagem;
9. Redução da quantidade de máquinas;
10. Aumento da vida útil de máquinas e ferramentas;
11. Aumento do controle sobre desgaste de ferramentas;
12. Alta flexibilidade de produção.
13. Aumento da repetibilidade das peças;
14. Maior segurança do operador; e
15. Redução do custo e produção mais rápida de protótipos de peças.

### O que é controle numérico?
Considera-se controle numérico (NC - Numerical Control) uma forma de automação programável de dispositivos capazes de dirigir os movimentos de posicionamento de um órgão mecânico em que os comandos relativos a esse movimento são elaborados de forma totalmente automática, a partir de informações numéricas ou alfanuméricas (números, letras ou outros símbolos) definidas, manualmente ou através de um programa.

#### Componentes básicos do NC
Um sistema de controle numérico consiste em três componentes básicos:

Programa de instruções;
Unidade de controle da máquina;
Equipamentos de processamento.

O programa de instruções são comandos detalhados passo a passo que direcionam o equipamento de processamento. Na sua forma mais comum, os comandos se referem à situação de um eixo de máquina-ferramenta com relação à mesa de trabalho na qual a peça é fixada. Instruções mais avançadas incluem a seleção de velocidades do eixo, ferramentas de corte, e outras funções.

unidade de controle da máquina (MCU) consiste na eletrônica e hardware de controle que lê e interpreta o programa de instrução e o converte em ações mecânicas da máquina-ferramenta ou outro equipamento.

equipamento de processamento É o componente que realiza um trabalho útil. é aquele que executa operações de usinagem, consistindo numa mesa de trabalho e eixos, bem como de motores e controles necessários para conduzi-los.

## 3.2 - Redes industriais
## 3.3 - Supervisórios

# Fontes
Este material foi baseado em: 
BAYER, Fernando Mariano; ECKHARDT, Moacir; MACHADO, Renato. Automação de Sistemas. Santa Maria: Universidade Federal de Santa Maria/Rede e-Tec, 2011.
Última atualização: quinta, 24 jun 2021, 11:02


