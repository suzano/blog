---
title: "Crontab"
date: 2023-01-06T22:49:41-03:00
draft: true
---

# Exemplo de funcionamento do crontab
crontab -e	Edita o crontab atual do usuário
crontab -l	Exibe o atual conteúdo do crontab do usuário
crontab -r	Remove o crontab do usuário

# Exemplos
1,21,41	*	*	*	*	comando (Toda hora, todo dia, nos minutos 1, 21 e 41)
30	4	*	*	1	comando (Toda segunda-feira, as 4:30 da manhã)
45	19	1,15	*	*	comando (Todo dia 1 e 15 às 19:45)
0-59/5 * * * * comando (Executar de 5 em 5 minutos)

# Espaços
Campo	Função
1o.	Minuto (0-59)
2o.	Hora (0-23)
3o.	Dia do mês (1-31)
4o.	Mês (1-12)
5o.	Dia da semana (0-6 (o “0” é domingo, “1” segunda, etc))
6o.	Programa pra execução

# Referências

