
---

# Aula: Redundância de Dados (Data Redundancy)

## 1. Introdução

Com o crescimento do uso de sistemas digitais, grandes quantidades de dados são armazenadas diariamente em bancos de dados, servidores e serviços em nuvem. Um dos conceitos importantes na gestão desses dados é a **redundância de dados**, que pode trazer tanto benefícios quanto problemas dependendo de como é utilizada.

A redundância de dados está relacionada à existência de **múltiplas cópias do mesmo dado em diferentes locais ou sistemas**. Esse fenômeno pode ocorrer de forma intencional ou não intencional dentro de um sistema de informação. ([IBM][1])

Compreender esse conceito é essencial para o desenvolvimento de sistemas, administração de bancos de dados e segurança da informação.

---

# 2. O que é Redundância de Dados

A **redundância de dados** ocorre quando **os mesmos dados são armazenados em mais de um lugar dentro de um sistema** ou em diferentes sistemas. 

Essas cópias podem existir:

* em diferentes bancos de dados
* em diferentes servidores
* em diferentes arquivos
* em sistemas distintos

### Exemplo simples

Tabela de clientes em dois sistemas diferentes:

| ID | Nome | Cidade    |
| -- | ---- | --------- |
| 01 | Ana  | Fortaleza |

Se esse mesmo registro existir em:

* Banco de dados do sistema de vendas
* Banco de dados do sistema de suporte

então existe **redundância de dados**.

---

# 3. Tipos de Redundância de Dados

A redundância pode ser classificada em dois tipos principais:

## 3.1 Redundância Intencional

É quando a duplicação de dados é **planejada e controlada**.

Ela é utilizada para melhorar:

* disponibilidade dos dados
* segurança
* recuperação de falhas

Por exemplo:

* backups
* replicação de banco de dados
* armazenamento em múltiplos servidores

Esse tipo de redundância ajuda a garantir que os sistemas continuem funcionando mesmo em caso de falha de hardware ou perda de dados. 

### Exemplo

Um banco de dados principal possui uma cópia de segurança em outro servidor.

Se o servidor principal falhar, o sistema continua funcionando com a cópia.

---

## 3.2 Redundância Não Intencional

Ocorre quando os dados são duplicados **sem planejamento**, geralmente por erros de modelagem ou armazenamento.

Esse tipo pode causar:

* inconsistência de dados
* aumento de custos de armazenamento
* dificuldades na atualização das informações

Por exemplo:

| Sistema   | Nome | Telefone  |
| --------- | ---- | --------- |
| Sistema A | João | 9999-9999 |
| Sistema B | João | 8888-8888 |

Nesse caso, existe **informação conflitante**, o que pode gerar erros nos sistemas.

---

# 4. Benefícios da Redundância Intencional

Quando bem planejada, a redundância pode trazer várias vantagens para os sistemas de informação.

## 4.1 Maior disponibilidade

Se um servidor falhar, outro servidor pode fornecer os dados.

Isso evita que o sistema fique fora do ar.

## 4.2 Segurança dos dados

Cópias redundantes ajudam a proteger dados contra:

* falhas de hardware
* corrupção de arquivos
* ataques cibernéticos

## 4.3 Continuidade dos sistemas

Sistemas críticos, como bancos ou hospitais, precisam funcionar continuamente.

A redundância garante que os dados permaneçam disponíveis.

## 4.4 Recuperação de desastres

Caso ocorra:

* falha de servidor
* exclusão acidental
* desastre físico

é possível recuperar os dados a partir de outra cópia. ([IBM][1])

---

# 5. Técnicas Utilizadas para Criar Redundância

Existem diversas tecnologias utilizadas para implementar redundância de dados.

## 5.1 Replicação de Dados

A **replicação de dados** consiste em criar cópias de um banco de dados em diferentes locais ou servidores.

Isso permite:

* acesso mais rápido
* tolerância a falhas
* maior disponibilidade

### Tipos de replicação

* **Síncrona** – dados são atualizados simultaneamente
* **Assíncrona** – atualização ocorre com pequeno atraso

---

## 5.2 RAID (Redundant Array of Independent Disks)

RAID é uma tecnologia que utiliza **múltiplos discos rígidos** para armazenar dados.

Exemplo:

* RAID 1 (espelhamento)

Os dados gravados em um disco são automaticamente copiados para outro.

Se um disco falhar, o outro mantém as informações.

---

## 5.3 Sistemas de Arquivos Distribuídos

Nesse modelo, os dados são armazenados em **diversos computadores (nós)**.

Se um nó falhar, os dados continuam acessíveis em outros.

Esse modelo é comum em:

* computação em nuvem
* big data
* grandes empresas de tecnologia

---

# 6. Problemas da Redundância Não Controlada

Quando a redundância não é gerenciada corretamente, pode causar vários problemas.

## 6.1 Aumento do custo de armazenamento

Mais cópias significam mais espaço em disco.

Em ambientes de nuvem isso pode aumentar bastante os custos.

---

## 6.2 Inconsistência de dados

Se uma informação for atualizada em um local e não em outro, os dados ficam diferentes.

Exemplo:

| Banco A     | Banco B     |
| ----------- | ----------- |
| João – 9999 | João – 8888 |

Qual é o telefone correto?

---

## 6.3 Queda de desempenho

Atualizar várias cópias pode tornar o sistema mais lento.

Principalmente em sistemas com muitos usuários.

---

## 6.4 Problemas de segurança

Quanto mais cópias existirem, maior o risco de:

* vazamento de dados
* acesso não autorizado

---

# 7. Como Reduzir Redundância Desnecessária

Existem técnicas para evitar redundância excessiva.

## 7.1 Normalização de Banco de Dados

A normalização organiza os dados em tabelas relacionadas para evitar duplicações.

Exemplo:

Tabela Clientes:

| ID | Nome |
| -- | ---- |

Tabela Pedidos:

| ID Pedido | ID Cliente |

Assim, os dados do cliente ficam armazenados apenas uma vez.

---

## 7.2 Deduplicação de dados

Processo que identifica dados duplicados e mantém apenas uma cópia.

Muito usado em:

* data centers
* backups
* armazenamento em nuvem

---

## 7.3 Compressão de dados

Reduz o tamanho dos dados removendo repetições.

Isso otimiza o uso de armazenamento.

---

## 7.4 Master Data Management (MDM)

Cria uma **fonte única de verdade para dados importantes**, como:

* clientes
* produtos
* funcionários

Isso evita múltiplas versões da mesma informação.

---

# 8. Redundância de Dados vs Recuperação de Dados

Apesar de parecerem semelhantes, são conceitos diferentes.

| Redundância             | Recuperação                   |
| ----------------------- | ----------------------------- |
| Estratégia preventiva   | Estratégia reativa            |
| Mantém cópias de dados  | Restaura dados perdidos       |
| Evita indisponibilidade | Corrige falhas após ocorrerem |

A redundância busca **garantir que os dados estejam sempre disponíveis**, enquanto a recuperação busca **restaurar dados após incidentes**.

---

# 9. Conclusão

A redundância de dados é um conceito fundamental na gestão de informações em sistemas computacionais. Quando aplicada corretamente, ela aumenta a segurança, disponibilidade e confiabilidade dos dados. Porém, quando ocorre de forma desorganizada, pode gerar inconsistências, custos elevados e problemas de desempenho.

Por isso, profissionais de tecnologia precisam saber **equilibrar redundância e eficiência no armazenamento de dados**.

---

# 10. Atividade para os alunos

### Questão 1

Explique com suas próprias palavras o que é redundância de dados.

### Questão 2

Qual a diferença entre redundância **intencional** e **não intencional**?

### Questão 3

Cite duas vantagens e dois problemas da redundância de dados.

### Questão 4

Explique como a **normalização de banco de dados** ajuda a reduzir redundância.

---


