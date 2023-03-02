# Archetype QUARKUS Cresol

Este projeto é o encarregado de garantir o modelo de arquitetura padronizada das 
nossas aplicações e criar um projeto pronto para uso utilizando a tecnologia quarkus e nativo para cloud.

## Pré requisitos

* JDK 11
* Maven 3.8.3 >
* 5-10 Minutos

## Instalação


```bash
mvn clean install
```

Quando o sistema for instalado, nosso archetype será disponibilizado na listagem
de possíveis executáveis no comando de geração de fontes do maven.

## Criando seu projeto QUARKUS cloud native

Em seu terminal, vá até sua workspace (diretório base dos seus projetos), e digite o seguinte comando:

```bash
mvn archetype:generate
```

Após executá-lo, o maven irá instalar as dependências necessárias em seu .m2 
para que o plugin gerador de código (nativo em versão 3.1.1) possa te listar os
archetypes disponíveis.

Se tudo deu certo até aqui, nosso archetype aparecerá ao final da lista como:
```bash
numero: local -> br.coop.cresol:archetype-quarkus-cresol (archetype-quarkus-cresol)
```
O número que aparece ao lado esquerdo é o que devemos digitar no terminal para 
que o maven execute nosso archetype corretamente.



## Finalizando a criação do projeto

Após executar nosso archetype, ele irá pedir 3 inputs, sendo:
* Nome do projeto a ser criado (tudo em minusculo e sem caracteres especiais)

## Testando nossa aplicação

## Pré requisitos

* JDK 11
* Maven 3.8.3 >
* lombok
* Docker
* Dcoker-compose


## Como rodar:

* Após finalizada a execução do comando 'archetype:generate' verifique se um novo projeto foi criado no seu workspace (diretório base dos seus projetos).
* Agora que o projeto está criado, só nos resta navegar até sua pasta raiz, e executar os seguintes comandos:

#####  Subindo dependências docker-compose:
    
```bash
docker-compose up
```

##### Empacotando o projeto:

```bash
mvn package 
```
OBS: Necessário executar o **package** antes quando estiver usando injeção de dependência do [mapstruct](https://mapstruct.org/)

##### Subindo o projeto:
 
```bash
mvn compile quarkus:dev
```
    
Na primeira vez que o comando é executado, o maven deve baixar as dependências do 
pom gerado para o projeto, então pode demorar alguns minutinhos, mas após 
primeira compilação e download de dependências, qualquer projeto quarkus gerado 
sobe em menos de 5 segundos!

Após a satisfação de dependências e subida da interface, nosso sistema está no ar!

Para verificar, acesse:

```bash
localhost:8090/${artifactId}
```

Se nada deu errado até aqui, devemos enxergar no navegador a página de boas vindas ao Quarkus Cresol.

Obs: Fique atento, pois nas documentações do Quarkus os comando são executados utilizando o maven embutido no próprio projeto, através do comando './mvnw'. 
Em nosso caso devemos usar o maven já instalado na máquina utilizando apenas o comando 'mvn'. 

Por padrão do nosso archetype, nossos projetos não possuem a pasta .mvn, que contém o maven embutido no projeto.

Não execute os comandos do Quarkus como 'sudo'. Caso você tenha feito isso e está ocorrendo o erro: 

```bash
[io.qua.dev.DevModeMain] Failed to start quarkus: java.lang.IllegalStateException: Failed to create cache dir 
```

Será necessário apagar a pasta de cache:

```bash
/tmp/vertx-cache
```

E rodar o comando novamente sem `sudo`.

### Informações importantes

* [Configuração lombok eclipse](https://projectlombok.org/setup/eclipse)
* Criação de tests unitario, integração e modo native
    * [tests-quarkus](https://quarkus.io/guides/getting-started-testing)
    * **@NativeImageTest** e **@QuarkusIntegrationTest** não suportam injeção de dependencias,portanto os tests nativos deveram ser tests de integração.
    * Os nomes das classes de tests nativos devem term com **IT**
    * Executando tests.
    `mvn verify ` ou `mvn test`
    * Executando tests no modo native.
    `mvn verify -Pnative`


#### Dependencias 

* Tolerance
    * [quarkus-smallrye-fault-tolerance](https://quarkus.io/guides/smallrye-fault-tolerance)
* Metrics 
    * [quarkus-micrometer](https://quarkus.io/guides/micrometer)
* DB-Migration 
    * [quarkus-flyway](https://quarkus.io/guides/flyway)
* Config Server 
    * [quarkus-spring-cloud-config-client](https://quarkus.io/guides/spring-cloud-config-client)
* Rest Client    
    * [quarkus-rest-client](https://quarkus.io/guides/rest-client)
* Messaging
    * [quarkus-smallrye-reactive-messaging](https://quarkus.io/guides/amqp)
* Health Check
    * [quarkus-smallrye-health](https://quarkus.io/guides/smallrye-health)
* Structured Log 
    * [quarkus-logging-json](https://quarkus.io/guides/logging)
* Container Image
    * [quarkus-container-image-jib](https://quarkus.io/guides/container-image)
* Percistence
    * [quarkus-hibernate-orm-panache](https://quarkus.io/guides/hibernate-orm-panache)
* Teste
    * [testcontainers](https://www.testcontainers.org/)
* Mapper
    * [mapstruct](https://mapstruct.org/)



 
   
    



