# Arquitetura Limpa na Prática

## Propósito do Desenvolvimento de Software

- O propósito do desenvolvimento de software é produzir impacto positivo de negócio, segundo Dan North — o inventor do Behaviour-Driven Development (BDD).
- Para atingir esse propósito, o objetivo do desenvolvimento de software é **minimizar o lead time de maneira sustentável**. 
	- Lead time é o tempo que se demora para, dado um problema, entregar-se uma solução para esse problema. Obviamente queremos minimizar esse tempo, entregando impacto positivo de negócio o mais rápido possível. 
	- Porém isso deve ser feito de uma maneira sustentável (ou seja, durável) para que o sistema tenha sobrevida longa.
- Note que os termos *minimizar* e *sustentável* na definição estão em oposição. É preciso encontrar um equilíbrio.

## O que é Arquitetura de Software

- De acordo com Robert Martin, o propósito da arquitetura de software é minimizar os recursos humanos necessários para construir e manter um sistema
	- Por meio da estratégia de deixar o máximo possível de opções em aberto, pelo máximo de tempo possível.
	- Facilitando o desenvolvimento, implantação, operação e manutenção do sistema construído. 
- "A arquitetura de um software é mais importante do que as suas funcionalidades. 
	- Uma implementação ruim de uma boa abstração não causa nenhum dano substancial à base de código. 
	- Mas uma abstração ruim ou camada faltando causa o apodrecimento de tudo" (Chris Kiehl - Amazon.
	-  Arquiteturas bem projetadas são fundamentais para a manutenção e a evolução de sistemas de software de maneira sustentável.

## Separação em camadas

- Um software complexo é composto por códigos em diferentes níveis de abstração.
- A médio e longo prazo, as porções de código de baixo nível, que tratam de **funcionalidades técnicas** e específicas de uma determinada tecnologia, tendem a mudar independentemente das **políticas de negócio** de alto nível do sistema, que tendem a ser mais estáveis.
- Uma boa arquitetura deve separar esses tipos de abstração em camadas, para que seja possível alterar os detalhes de implementação de baixo nível sem que as regras de negócio de alto nível sejam afetadas por essas alterações, e vice-versa. 
- Em essência, se trata da separação de interesses. Isso está diretamente relacionado com os princípios de projeto S.O.L.I.D., em particular com o princípio da Inversão de Dependência (Dependency Inversion Principle): abstrações de alto nível não devem depender de concreções de baixo nível.

## Arquitetura plugável

- Tanto Martin quanto Dan North acreditam que o melhor tipo de arquitetura é aquele que maximiza a possibilidade de se trocar seus componentes — uma arquitetura plugável.
	- o cerne do sistema fica no centro e desacoplado dos diversos plug-ins que implementam detalhes de baixo nível. 
	- Esses plug-ins podem ser plugados, desplugados e substituídos por outros plug-ins conforme a necessidade.

## Regras de negócio são centrais

- As regras de negócio são as políticas que permitem uma empresa ganhar ou economizar dinheiro. 
	- É o que gera valor para quem utiliza os serviços daquele negócio. 
	- As regras de negócio são o que há de mais importante em um sistema de software. 
- Existem dados e políticas que são críticas ao negócio e que existiriam mesmo que não houvesse um sistema que os implementasse.
	- A junção entre os dados críticos de negócio com as regras críticas de negócio formam as **Entidades do Domínio**.
- Nem todas as regras de negócio implementadas em um sistema são tão puras e essenciais quanto as regras de negócio do domínio.
	- Existem regras de negócio atreladas a forma como o sistema automatiza as regras de negócio do domínio.
	- Essas são as regras de negócio da aplicação e, de maneira geral, constituem os **Casos de Uso**, que são as operações de alto nível realizadas pelos interessados no sistema.

## DDD: Domain-Driven Design

- Abordagem para desenvolver os sistemas com ênfase no domínio de negócios (é tanto chave no DDD quanto na Arquitetura Limpa)
- Torna os sistemas mais resilientes, já que a parte central deles é desenvolvida de maneira testável e independente dos outros interesses.
- Segundo Robert Martin, a arquitetura de um sistema deveria 'gritar' o seu propósito, e não revelar facilmente detalhes de baixo nível de como o sistema é implementado.
	- Ou seja, o que deveria ser mais evidente no sistema é o seu propósito e não as tecnologias utilizadas para implementá-lo, e nem seus detalhes de mais baixo nível.

## Bases da Arquitetura Limpa

- Segundo Robert Martin, seu idealizador, a Arquitetura Limpa é uma tentativa de integrar várias arquiteturas desenvolvidas nas últimas décadas em uma ideia prática.
- As arquiteturas que embasaram a Arquitetura Limpa incluem a Arquitetura Hexagonal (também conhecida como Portas e Adaptadores); a Dados, Contexto e Interação (DCI); e a Fronteiras, Controle e Entidade (BCE).

### Arquitetura Hexagonal (Portas e Adaptadores)

- O alto acoplamento entre regras de negócio, interface gráfica e dispositivos externos (como banco de dados) dificulta a realização de testes automatizados ou a execução da aplicação sem a interface gráfica.
- Desenvolvida por Cockburn, a Arquitetura Hexagonal desacopla o cerne da aplicação (regras de negócio) de quem a executa (usuários, programas, testes) e também de quem ela conversa (dispositivos e bancos de dados).
	- Possibilita que uma aplicação seja executada a partir de usuários, programas, testes automatizados ou scripts e seja desenvolvida e testada isolada de seus dispositivos e bancos de dados necessários em tempo de execução. 
- A parte interna da aplicação se comunica com a parte externa por meio de portas (interfaces) que são ajustadas por meio de adaptadores conforme os dispositivos específicos.

### DCI (Dados, Contexto e Interação)

- O DCI leva à construção de arquiteturas que estendem a programação orientada a objetos contemporânea de sua estrutura centrada nos dados para focar mais no valor de negócios de operações em nível de sistema – os casos de uso. 
- Nesse sentido ela casa muito bem com ideias essenciais da Arquitetura Limpa como, por exemplo, dar papel de destaque para os casos de uso na estrutura do sistema.

### BCE (Fronteira, Controle e Entidade)

- O padrão arquitetural Fronteira, Controle e Entidade (do Inglês, Boundary, Control, Entity — BCE) foi desenvolvido por Ivar Jacobson a partir de sua abordagem de engenharia de software orientada a objetos guiada por casos de uso. 
- O BCE estrutura as classes que compõem o sistema a partir de suas responsabilidades na realização dos casos de uso.
- Temos o modelo de domínio nas Entidades, a comunicação com o mundo externo a partir das Fronteiras e a implementação dos casos de uso e das regras de negócio da aplicação nos Controles.

*****

## Princípios da Arquitetura Limpa

![[Pasted image 20230224103807.png]]

- A idéia da Arquitetura Limpa é proteger as regras de negócio no core da arquitetura e deixar o uso de bibliotecas e frameworks na periferia da arquitetura.
- A cada camada indo de dentro para fora, podemos perceber mais detalhes de implementação, mais tecnologia e infraestrutura.
- Cada uma das camadas da arquitetura pode ser testada em isolamento.
- A aplicação se torna independente da Interface Gráfica e do banco de dados.
- Tudo isso só é possível graças a **Regra de Dependência**: as dependências de código-fonte só podem apontar para dentro, em direção às políticas de alto nível (e nunca para fora).

### Camadas

#### Entidades
- Representam as regras de negócio do domínio.
- São as partes do sistema com menor probabilidade de serem alteradas quando algo muda externamente.
- Por estarem isoladas, podem ser utilizadas por diversas aplicações na empresa.

#### Casos de Usos
- Os casos de uso orquestram o fluxo de dados de e para as entidades, e direcionam essas entidades a utilizarem suas regras de negócio críticas para atingirem os objetivos do caso de uso.
- Espera-se que mudanças nessa camada não afetem as entidades.

#### Adaptadores de Interface
- Os adpatadores convertem os dados no formato mais conveniente para os casos de uso e entidades para o formato mais conveniente para algum agente externo (como o banco de dados ou a Web).

#### Frameworks e Drivers
- Na camada mais externa entram os detalhes sujos de implementação (frameworks, bibliotecas e outras ferramentas), onde eles podem causar pouco prejuízo caso sejam alterados.
- Como discutido por Robert Martin, o banco de dados e a web são apenas detalhes.
- Geralmente os desenvolvedores do sistema não escreverão código nesta camada.

#### Main
- Segundo Robert Martin, o componente Principal (ou Main) implementa a política de mais baixo nível no sistema e é o ponto de entrada do sistema.
- O trabalho desse componente é criar todos os Factories, Strategies e outros serviços globais, e entregá-los às porções de alto nível mais abstratas do sistema.
- Otávio Lemos considera o Main uma quinta camada responsável por configurar e executar o sistema, fazendo todas as conexões entre as interfaces, adaptadores e as implementações concretas.


## Arquitetura Limpa no Frontend

- Na opinião de Otávio Lemos, como o frontend implementa a interface gráfica, ele já faz parte da camada mais externa da arquitetura.
	- Trata-se de tecnologias específicas, ou seja, código de baixo nível, não faz sentido aplicar rigorosamente a Regra de Depedência e não valeria a pena replicar todas as camadas da Arquitetura Limpa no frontend.
	- Separar o backend do frontend já representa o maior ganho, por tornar o sistema independente de interfaces gráficas (cliente Web, aplicação mobile, console).
- Todos os princípios S.O.L.I.D. e as boas práticas de projeto continuam valendo para o Frontend.
	- Um bom padrão de projeto para ser utilizado no frontend é o Humble Object.
	- Otávio recomenda o trabalho de <label class="ob-comment" title="" style=""> Khalil Stemmler <input type="checkbox"> <span style=""> Pesquisar a respeito de Khalil Stemmler, parece uma boa referência internacional para Typescript e DDD no Frontend </span></label>, ele possui um [guia de arquitetura para o lado do cliente](https://khalilstemmler.com/articles/typescript-domain-driven-design/ddd-frontend/) em seu blog.
