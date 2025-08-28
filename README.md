# Coleção de Utilitários para Integração MT4-Python

Esta pasta serve como um repositório de bibliotecas e ferramentas de suporte, essenciais para projetos que envolvem a comunicação e integração entre a plataforma MetaTrader (MT4/MT5) e scripts Python.

O objetivo é manter ferramentas úteis e reutilizáveis que resolvem problemas comuns nesse tipo de integração.

## Conteúdo Atual

Atualmente, esta coleção inclui os seguintes utilitários:

### 1. AlertSpy
- **O que é?** Um projeto em C++ que compila para uma DLL (`AlertSpy.dll`).
- **Finalidade:** Permitir que um Expert Advisor (EA) em execução no MT4 consiga "ler" o texto de caixas de alerta que aparecem na tela. É extremamente útil para capturar sinais de indicadores ou EAs que só se comunicam através de alertas visuais.
- **Como usar:** Consulte o `README.md` dentro da pasta `AlertSpy` para instruções detalhadas de compilação e uso.

### 2. mql-zmq-master
- **O que é?** Uma cópia da biblioteca `mql-zmq`.
- **Finalidade:** Fornece uma ponte de comunicação de alta velocidade e baixa latência entre o MQL (a linguagem do MetaTrader) e outras aplicações, usando a tecnologia ZeroMQ. É a base para a troca de mensagens, sinais e dados em tempo real entre o MT4 e o nosso robô em Python.
- **Fonte Original:** [dingmaotu/mql-zmq](https://github.com/dingmaotu/mql-zmq)

## Futuro

Este repositório de suporte pode ser expandido no futuro com novas ferramentas, scripts e bibliotecas para aprimorar a integração entre o ecossistema MQL e Python.
