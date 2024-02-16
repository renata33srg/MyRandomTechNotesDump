# Arquitetura Hexagonal

Consiste no modelo de portas e adaptadores, onde separamos completamente nosso domínio de negócio de componentes externos, permitindo um alto nível de desacoplamento.  

Em um primeiro momento, quando começamos a utilizar este padrão a percepção de uso pode parecer a de implementar muito código para pouco resultado, porém, o ganho real vem com o tempo, onde se torna extremamente perceptível a velocidade que ganhamos no desenvolvimento de novas funcionalidades e torna a manutenibilidade do que já existe mais simples.  

Um outro fator interessante é que com este padrão arquitetural conseguimos plugar e desplugar qualquer componente externo ao nosso domínio com o mínimo de esforço e sem grandes preocupações e ficamos isentos de dependências de fatores externos como por exemplo frameworks.  

Projeto para exemplificar essa arquitetura (utilizando a linguagem Go) no GitHub: https://lnkd.in/dq5BW5nT.  