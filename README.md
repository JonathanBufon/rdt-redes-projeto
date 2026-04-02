# Trabalho de Redes

## Implementação de um RDT utilizando Grafos (Camada de Transporte)

---

## 📌 Objetivo

Desenvolver uma aplicação que simula o funcionamento de protocolos de **Transferência Confiável de Dados (RDT)** sobre uma rede representada por **grafos ponderados**, incluindo fragmentação de arquivos e escolha de melhor caminho.

---

## 🧱 Arquitetura

A aplicação será dividida em duas camadas principais:

* **Frontend (React.js)**
* **Backend (API em Python)**

### 🔄 Ciclo de Vida

Serão implementados **hooks com lifecycle**, permitindo controle das etapas do envio de dados:

* Inicialização
* Envio de pacotes
* Recebimento de ACKs
* Reenvio em caso de falha
* Finalização da transmissão

---

## 📡 RDTs (Reliable Data Transfer)

Serão implementadas múltiplas versões de RDT seguindo o princípio **DRY (Don’t Repeat Yourself)**:

* Reutilização de código entre versões
* Separação de responsabilidades
* Estrutura modular para evolução dos protocolos

Exemplos de versões possíveis:

* RDT 1.0
* RDT 2.0
* RDT 3.0

---

## 🎲 Algoritmo de Parâmetros Aleatórios

Para simular condições reais de rede, será implementado um mecanismo de aleatoriedade baseado em **porcentagem de perda/corrupção de pacotes**.

### Funcionamento

* Durante a geração do grafo, será definido um parâmetro global de perda (ex: 35%)
* Cada pacote (JSON) terá um atributo chamado `DROP`
* Esse atributo define a probabilidade de o pacote ser:

  * Perdido
  * Corrompido
  * Entregue com sucesso

### Lógica de Decisão

O algoritmo funcionará de forma semelhante a um **dado (ex: D20)**:

* Um valor aleatório será gerado a cada envio de pacote
* Esse valor será comparado com a porcentagem definida
* Com base nisso, o sistema decide o destino do pacote

### Exemplo

* Pacote com ID: `xyz`
* Probabilidade de falha: **35%**

Resultado possível:

* 35% → pacote perdido ou corrompido
* 65% → pacote entregue com sucesso

Esse mecanismo será essencial para testar a robustez dos protocolos RDT implementados.

---

## 🧮 Algoritmo de Melhor Caminho

A comunicação entre os nós da rede será baseada em:

### Grafos Ponderados

* Cada nó representa um ponto da rede
* Cada aresta possui um peso (latência, custo, etc.)

Será utilizado o algoritmo de **Dijkstra** para encontrar o melhor caminho entre origem e destino.

---

## 🔗 Comunicação entre Frontend e Backend

A API será responsável por intermediar a comunicação com o frontend.

### Fluxo:

1. O frontend solicita a criação de um grafo:

   * Aleatório
   * Ou definido por parâmetros (nós e arestas)

2. O usuário define:

   * Remetente
   * Destinatário
   * Nome do arquivo
   * Extensão
   * Tamanho

3. O backend:

   * Processa os dados
   * Fragmenta o arquivo
   * Inicia o envio dos pacotes

---

## ⚙️ Funcionamento do Backend

O backend será responsável por:

* Fragmentar o arquivo com base no tamanho definido
* Ordenar os pacotes
* Aplicar as regras dos protocolos RDT
* Garantir confiabilidade na entrega

Cada pacote será representado como um objeto JSON:

```json
{
  "id": "xyz",
  "arquivo": "nome_arquivo.extensao",
  "tamanho": "tamanho_fragmento"
}
```

Os pacotes serão enviados ao frontend para visualização do processo.

---

## 🧰 Stack Tecnológica

### Backend

* Python
* Biblioteca de grafos com suporte ao algoritmo de Dijkstra

### Frontend

* React.js

---

## 🚀 Considerações Finais

Este projeto permite visualizar e compreender conceitos fundamentais de redes de computadores, como:

* Protocolos de transporte confiáveis (RDT)
* Fragmentação de dados
* Controle de erros e retransmissão
* Algoritmos de roteamento

Além disso, promove boas práticas de desenvolvimento como:

* Código reutilizável (DRY)
* Arquitetura modular
* Separação entre frontend e backend

---

## 📎 Possíveis Extensões Futuras

* Simulação de perda de pacotes
* Introdução de atraso na rede
* Interface gráfica mais interativa
* Comparação entre diferentes algoritmos de roteamento
