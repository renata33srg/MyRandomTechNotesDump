# Conceitos básicos de Engenharia de Software / DevOps

## O que é PR/merge? 

- Merge  
  - Imagine que você e seu amigo estão desenhando em um grande papel, cada um em um lado. Quando ambos terminam, vocês querem juntar os desenhos para criar uma obra-prima. No mundo da programação, "merge" é basicamente isso: combinar as alterações feitas em diferentes versões de um arquivo (ou projeto) para criar uma versão final unificada. É como fazer um aperto de mão entre códigos!

- PR
  - PR significa Pull Request. Imagine que você fez um bolo incrível e quer que seus amigos o provem e deem sua opinião antes de levá-lo à festa. Você faz um "pedido para que puxem" uma fatia e avaliem. No mundo do desenvolvimento de software, é assim que você diz: "Ei, olhem o que eu programei! Está bom para incluir no nosso projeto?".
  
---
 
## Qual é a diferença entre endpoint e API?

### API (Interface de Programação de Aplicativos) 
- É um conjunto completo de regras e especificações para troca de informação de um usuário/sistema com um servidor/sistema. É como um garçom em um restaurante: ele sabe como levar seu pedido para a cozinha e trazer de volta o que você pediu.

### Endpoint
- É o ponto específico para o acesso a essas informações que serão manipuladas pela API. É como a mesa específica onde você está sentado no restaurante ou a cozinha onde seu pedido é feito. Cada pedido que você faz (por exemplo, para pegar o cardápio ou pedir um prato) vai para um "ponto final" específico.

Em resumo, a API é o conjunto completo de regras e especificações para trocar informações, enquanto os endpoints são os pontos específicos de acesso para essas informações.

---

## O que são os verbos HTTP? Get, Post etc. 

Para entender esse tema, primeiro é necessário entender o que é um recurso e uma coleção de recursos: no contexto do DDD (Domain Driven Design - Desenvolvimento Orientado a Domínio, um recurso é uma entidade que representa uma parte específica de um domínio funcional. O recurso é uma instância única, com características e identidades próprias, atuando como um componente individual dentro do sistema mais amplo. A coleção é um conjunto que pode ser usado para definir os subdomínios dos recursos, ou seja, distinguir a que o conjunto de recursos se refere.

GET, POST, PATCH, PUT e DELETE são algumas das palavras usadas em Tecnologia para definir certos comportamentos que APIs realizarão em algum recurso. 
Essa interação com os recursos é chamada de ação e, por esse motivo, essas operações são chamadas de "verbos HTTP". Semânticamente, os verbos são uma classe de palavra da linguagem natural que denotam a "realização de alguma ação".

Cada verbo HTTP é responsável por uma ação específica, que pode ou não ser "repetível", isto é, pode ou não ser executada várias vezes e ter o mesmo resultado no final (idempotência)
	
### GET, a consulta
- Você e seu amigo chegaram ao restaurante, sentaram-se à mesa e solicitaram ao garçom o cardápio para poder escolher os pedidos. Você e seu amigo acabaram de fazer um GET (consulta) de informação.
		
### POST, a solicitação da criação
- Após ler as informações do cardápio e decidir o que comer, vocês disseram ao garçom quais seriam os pedidos. Ele anotou tudo em uma comanda e levou os pedidos para a cozinha para que fossem preparados. Você e seu amigo acabaram de fazer um POST (solicitação de criação) de informação.
		
### PATCH, a alteração parcial da informação e PUT, a alteração total da informação
- Um tempo depois, você decidiu que quer trocar um dos ingredientes do seu pedido e seu amigo mudou de ideia a respeito do que quer comer e decidiu pedir outra coisa do cardápio. Vocês chamam o garçom e solicitam as alterações/substituições desejadas. Você acabou de fazer um PATCH (solicitação de alteração parcial) e seu amigo acabou de fazer um PUT (solicitação de alteração total) das informações. 

### DELETE, a remoção da informação
- Seu amigo recebeu uma ligação urgente do trabalho e precisou ir embora do restaurante. Você ficou sozinho e não vai conseguir comer a parte que seria do seu amigo no pedido, então você chama o garçom e solicita o cancelamento do pedido do seu amigo. Você acabou de fazer um DELETE (solicitação de remoção) da informação.

---  

## O que é um programa do mainframe?
Mainframe é como um supercomputador que faz o trabalho pesado para grandes empresas, cuidando de toneladas de dados e operações críticas. Um programa de mainframe é um software que roda nesse gigante, fazendo tarefas importantes, como processar transações bancárias ou reservas de voos.

## O que é o processamento batch do mainframe?
Processamento batch (ou em lote) no mainframe é a junção de um monte de tarefas ou dados, que, por criticidade ou característica dos processos executados, são colocados para processar todos juntos durante a noite (ou quando o mainframe estiver menos ocupado). Ao final desse processamento em lotes, tudo está pronto de uma vez.
É como fazer a lavanderia para a semana inteira de uma só vez, em vez de uma peça de roupa por dia.

## Diferença entre os ambientes de desenvolvimento, homologação, piloto e produção

**Desenvolvimento**: É a mesa de trabalho do programador, onde ele cria e testa novas ideias.

**Homologação/Testes**: É como um ensaio geral antes da estreia da peça, onde tudo é testado para garantir que funcione bem.

**Piloto**: É um "teste de campo" com um grupo menor de usuários finais antes de lançar para todo mundo, como uma pré-estreia de um filme.

**Produção**: O show ao vivo! Onde o software roda de verdade, servindo aos usuários.


## Cloud governada x autogovernada​​

- Cloud governada: Imagine que você mora em uma cidade com regras estritas sobre o que pode e o que não pode fazer. Aqui, a infraestrutura de nuvem é gerenciada com políticas e regras rigorosas para garantir segurança e conformidade.
- Cloud autogovernada: Agora, imagine que você vive em uma comunidade com menos regras, onde as pessoas têm mais liberdade para gerenciar suas coisas. Neste modelo, os usuários têm mais controle e responsabilidade sobre sua infraestrutura na nuvem.

## O que é o Veracode?
Veracode é como um detetive de segurança para o seu código. Ele escaneia e procura por pistas (vulnerabilidades) que possam permitir a invasores causar problemas. Depois, dá dicas sobre como consertar essas falhas antes que os "bandidos" possam explorá-las.

## O que é o Silk?
Silk pode se referir a muitas coisas, mas no mundo da tecnologia, geralmente está relacionado ao Silk Test, uma ferramenta que ajuda a verificar se o software funciona como deveria, testando automaticamente as aplicações. É como um robô que verifica todos os botões e funções para garantir que tudo esteja em ordem antes de você usá-lo.

