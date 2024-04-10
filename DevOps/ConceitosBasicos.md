# Conceitos básicos de Engenharia de Software / DevOps

## O que é PR/merge? 

- PR
  - PR significa Pull Request. Imagine que você fez um bolo incrível e quer que seus amigos o provem e deem sua opinião antes de levá-lo à festa. Você faz um "pedido para que puxem" uma fatia e avaliem. Em TI, é assim que são solicitadas as opiniões (revisões) dos colegas: "Ei, olhem o que eu programei! Está bom para incluir no nosso projeto?".

- Merge  
  - Imagine que você e seu amigo estão montando peças de lego, cada um fazendo um objeto. Quando ambos terminam, vocês querem juntar as peças montadas para criar algo maior, então vocês "mesclam" as os dois objetos. No mundo da programação, "merge" é basicamente isso: combinar as alterações feitas em diferentes versões de um arquivo (ou projeto) para criar uma versão final unificada. 


  
---
 
## Qual é a diferença entre endpoint e API?

### API (Interface de Programação de Aplicativos) 
- É um conjunto completo de regras e especificações para troca de informação de um usuário/sistema com um servidor/sistema. É como um garçom em um restaurante: ele sabe como levar seu pedido para a cozinha e trazer de volta o que você pediu.

### Endpoint
- É o ponto específico para o acesso a essas informações que serão manipuladas pela API. É como a mesa específica onde você está sentado no restaurante ou a cozinha onde seu pedido é feito. Cada pedido que você faz (por exemplo, para pegar o cardápio ou pedir um prato) vai para um "ponto final" específico.

Em resumo, a API é o conjunto completo de regras e especificações para trocar informações, enquanto os endpoints são os pontos específicos de acesso para essas informações.

---

## Qual a diferença entre esteira e pipeline? O que é o CodePipeline?

- Pipeline, a sequência de etapas técnicas para entrega de código

  Um pipeline é uma cadeia de processos automatizados pelos quais o código-fonte passa para se tornar um produto de software pronto. Esses processos incluem compilação, testes (unitários e de integração), análise de bugs/vulnerabilidades, implantação, entre outros. 
  Um pipeline é projetado para ser automatizado, reproduzível e consistente, garantindo que o código que chega ao usuário final seja de alta qualidade e esteja livre de erros conhecidos.
  Imagine um pipeline (ou tubulação) em uma fábrica de chocolates. Os chocolates passam por várias etapas na tubulação: desde a mistura dos ingredientes, moldagem, resfriamento, até a embalagem. Cada etapa é necessária para transformar os ingredientes brutos em deliciosos chocolates prontos para venda.

- Esteira, o processo automatizado de entrega de software  
   O termo "esteira" muitas vezes é usado de forma intercambiável com pipeline, especialmente quando falamos sobre esteira de integração e entrega contínua (CI/CD - Continuous Integration/Continuous Delivery).
   No entanto, o conceito de esteira pode ser visto de forma mais ampla, abrangendo não apenas o pipeline de CI/CD, mas também o processo contínuo e automatizado de levar o código do desenvolvimento à produção, incluindo integração, entrega, implantação e feedback. A esteira enfatiza o movimento contínuo e a automação em todas as etapas do ciclo de vida do desenvolvimento de software.
   A palavra "esteira" evoca a imagem de uma esteira rolante, como aquelas usadas em aeroportos para bagagens ou em supermercados no caixa. Ela transporta itens de um ponto a outro de forma contínua e sem interrupções.

Resumindo
Pipeline: Refere-se especificamente à cadeia de processos pelos quais o código passa para se tornar um produto pronto. É uma parte crucial da automação em CI/CD, focando nas etapas técnicas de processamento do código.
Esteira: Embora muitas vezes usado como sinônimo de pipeline em discussões sobre CI/CD, pode ser entendido de forma mais ampla como o sistema ou a abordagem que engloba todo o processo de movimento contínuo do código, desde o desenvolvimento até a produção, promovendo a automação e a eficiência em todo o ciclo de vida do desenvolvimento de software.
Em resumo, enquanto o pipeline é uma sequência específica de etapas técnicas, a esteira pode ser vista como o conceito mais amplo que abrange não apenas o pipeline, mas todo o processo contínuo e automatizado de desenvolvimento e entrega de software.

#### E onde entra o CodePipeline nessa história?

O Code Pipeline é uma ferramenta da AWS que automatiza os passos para a construção de um pipeline, permitindo incluir/alterar etapas que são executadas nas entregas de código.


---

## O que são os verbos HTTP? Get, Post etc. 

Para entender esse tema, primeiro é necessário entender o que é um recurso e uma coleção de recursos: no contexto do DDD (Domain Driven Design - Desenvolvimento Orientado a Domínio, um recurso é uma entidade que representa uma parte específica de um domínio funcional. O recurso é uma instância única, com características e identidades próprias, atuando como um componente individual dentro do sistema mais amplo. A coleção é um conjunto que pode ser usado para definir os subdomínios dos recursos, ou seja, distinguir ao que o conjunto de recursos se refere.

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

---

## O que é o processamento batch do mainframe?
Processamento batch (ou em lote) no mainframe é a junção de um monte de tarefas ou dados, que, por criticidade ou característica dos processos executados, são colocados para processar todos juntos durante a noite (ou quando o mainframe estiver menos ocupado). Ao final desse processamento em lotes, tudo está pronto de uma vez.
É como fazer a lavanderia para a semana inteira de uma só vez, em vez de uma peça de roupa por dia.

---

## Diferença entre os ambientes de desenvolvimento, homologação, piloto e produção

**Desenvolvimento**: É o backstage de uma peça de teatro, onde é possível criar e testar novas ideias/implementações.

**Homologação/Testes**: É como um ensaio geral no teatro vazio antes da estreia de uma peça, onde tudo é testado por todos os envolvidos para garantir que funcione bem.

**Piloto**: É um "teste de campo" com um grupo menor de telespectadores antes de lançar a peça para todo mundo (é como a pré-estreia de um filme).

**Produção**: É a hora do show!  Onde o teatro está cheio de telespectadores e a peça será apresentada em sua completude. 

---

## Cloud governada x autogovernada​​

- Cloud governada: Imagine que você mora em uma cidade com regras estritas sobre o que pode e o que não pode fazer. Aqui, a infraestrutura de nuvem é gerenciada com políticas e regras rigorosas para garantir segurança e conformidade.
- Cloud autogovernada: Agora, imagine que você vive em uma comunidade com menos regras, onde as pessoas têm mais liberdade para gerenciar suas coisas. Neste modelo, os usuários têm mais controle e responsabilidade sobre sua infraestrutura na nuvem.

---

## O que é o Veracode?
Veracode é como um detetive de segurança para o seu código. Ele escaneia e procura por pistas (vulnerabilidades) que possam permitir a invasores causar problemas. Depois, dá dicas sobre como consertar essas falhas antes que os "bandidos" possam explorá-las.

---

## O que é o Silk?
O Silk é uma ferramenta que ajuda a verificar se o software funciona como deveria, testando automaticamente as aplicações. É como um robô que verifica todos os botões e funções para garantir que tudo esteja em ordem antes de você usá-lo.

---

## Lambda

Uma Lambda pode ser definida de acordo com dois tópicos diferentes: programação funcional e cloud AWS.
Na programação funcional, a Lambda é como um ninja: ele aparece rapidamente, executa uma tarefa específica com precisão e desaparece. Refere-se a uma função que é definida sem um nome (função anônima) e pode ser usada onde você precisar realizar uma operação rápida e simples, como uma pequena missão secreta.

Na cloud AWS, a Lambda é como um super-herói dos filmes, sempre pronto para salvar o dia. Ele não fica por aí esperando as coisas acontecerem; em vez disso, ele é convocado apenas quando necessário. Quando surge um problema específico (um evento), ele aparece instantaneamente, usa seus superpoderes (executa o código) para resolver a situação com precisão, e depois desaparece sem deixar rastros, aguardando a próxima chamada.
Em outras palavras, a Lambda é um serviço da AWS que permite executar códigos em resposta a eventos específicos, sem a necessidade de provisionar ou gerenciar servidores, isto é, sem a necessidade do usuário inicializar uma máquina para executar o código. Você simplesmente carrega seu código, que pode realizar tarefas como acessar bancos de dados, iniciar e parar outros serviços da AWS, modificar arquivos no Amazon S3, e mais. A Lambda se encarrega de executar esse código com alta disponibilidade, cuidando de tudo, desde a administração do sistema até o escalonamento automático. É como ter um super-herói da computação ao seu dispor, capaz de realizar qualquer tarefa que você designar, grande ou pequena, sempre pronto para a ação quando o "sinal" (trigger) é ativado.

---

## Tópico
Em uma conversa, um "tópico" é sobre o que você está falando, isto é, um assunto ou categoria que define o tipo de informação ou mensagem sendo enviada e recebida. 
Em tecnologia, o conceito é semelhante: um tópico é como se fosse um canal de TV para o seu código sintonizar e receber informações.

---

## Prometheus?​​
É uma ferramenta que monitora e alerta para sistemas de computação. Ele "vigia" sua infraestrutura tecnológica para garantir que tudo esteja funcionando corretamente, como um guarda de trânsito que garante que não haja congestionamentos nos dados.
