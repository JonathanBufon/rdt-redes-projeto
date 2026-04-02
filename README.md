# RDT com Grafos — Simulação de Transporte Confiável

## Visão Geral

Aplicação para simular protocolos de Transferência Confiável de Dados (RDT) sobre uma rede modelada como grafo ponderado. O sistema permite observar, de forma visual e controlada, o envio de pacotes, perdas, retransmissões e escolha de rotas.

---

## Objetivo

Simular o comportamento da camada de transporte com foco em:

* Confiabilidade na entrega de dados
* Fragmentação de arquivos
* Controle de erros e retransmissão
* Roteamento baseado em menor custo

---

## Arquitetura

Separação clara entre responsabilidades:

```
Frontend (React)
    ↓
API (Python)
    ↓
Motor de Simulação (RDT + Grafos)
```

### Frontend

* Interface visual da rede (grafo)
* Configuração da transmissão
* Exibição do fluxo de pacotes em tempo real

### Backend

* Geração e manipulação do grafo
* Execução dos algoritmos de roteamento
* Implementação dos protocolos RDT
* Simulação de falhas de rede

---

## Protocolos RDT

Implementação modular e evolutiva:

* RDT 1.0 — Canal perfeito
* RDT 2.0 — Detecção de erros (ACK/NAK)
* RDT 3.0 — Retransmissão com timeout

Estratégia:

* Reutilização de código
* Isolamento por responsabilidade
* Extensibilidade para novas variações

---

## Simulação de Rede

### Modelo

* Grafo ponderado
* Nós → dispositivos
* Arestas → conexões com custo (latência)

### Roteamento

* Algoritmo de Dijkstra
* Cálculo do menor caminho entre origem e destino

---

## Simulação de Falhas

Cada pacote possui comportamento probabilístico.

Parâmetros:

* Taxa de perda
* Taxa de corrupção

Execução:

* Geração de valor aleatório por pacote
* Decisão baseada em threshold

Estados possíveis:

* Entregue
* Perdido
* Corrompido

---

## Fluxo de Execução

1. Definição do grafo (aleatório ou manual)
2. Configuração da transmissão:

   * Origem
   * Destino
   * Arquivo
   * Tamanho
3. Fragmentação dos dados
4. Envio dos pacotes
5. Recebimento de ACK/NAK
6. Retransmissões quando necessário
7. Finalização

---

## Estrutura de Pacote

```json
{
  "id": "string",
  "arquivo": "string",
  "tamanho": "number",
  "status": "sent | lost | corrupted | delivered"
}
```

---

## Stack

**Frontend**

* React

**Backend**

* Python
* Biblioteca de grafos (ex: NetworkX)

---

## Execução

### Backend

```bash
cd backend
pip install -r requirements.txt
python app.py
```

### Frontend

```bash
cd frontend
npm install
npm start
```

---

## Extensões

* Simulação de atraso (latência variável)
* Controle de janela (Sliding Window)
* Comparação entre algoritmos de roteamento
* Persistência de simulações
* Visualização temporal (timeline de eventos)

---

## Finalidade Acadêmica

Projeto voltado para compreensão prática de:

* Camada de transporte
* Protocolos confiáveis
* Redes baseadas em grafos
* Tolerância a falhas

Foco em experimentação e visualização do comportamento dos protocolos.

---

## Referências e Documentação

- Graph Theory (conceitos fundamentais de grafos):  
  [Graph Theory Tutorial](https://www.geeksforgeeks.org/visualize-graphs-in-python/?utm_source=chatgpt.com)  

- NetworkX (biblioteca para manipulação de grafos em Python):  
  [NetworkX Python Package](https://www.geeksforgeeks.org/python/networkx-python-software-package-study-complex-networks/?utm_source=chatgpt.com)  

- Visualização de grafos com NetworkX + Matplotlib:  
  [Visualize Graphs with NetworkX](https://www.geeksforgeeks.org/python/python-visualize-graphs-generated-in-networkx-using-matplotlib/?utm_source=chatgpt.com)  

