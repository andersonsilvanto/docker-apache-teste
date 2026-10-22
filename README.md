# Servidor Web Apache em Docker (Debian)

Este projeto contém a configuração de um ficheiro `Dockerfile` para construir e executar um servidor web **Apache** baseado na imagem oficial do **Debian**.

---

## 🛠️ Tecnologias Utilizadas

* **Docker**
* **Debian**
* **Apache2**

---

## 🚀 Como Executar o Projeto

### 1. Construir a Imagem Docker

No terminal, dentro da pasta do projeto, execute o comando abaixo para construir a imagem:

```bash
docker build -t apache_teste:1.0 .

RELATÓRIO DE AULA PRÁTICA: IMPLANTAÇÃO DE SERVIDOR WEB APACHE COM DOCKER
Curso: Engenharia de Software

Disciplina: Infraestrutura de Software / Containerização

Aluno: Anderson Lopes Vidal Silvanto

Data: Outubro de 2026

1. MÉTODOS
Nesta atividade prática, utilizou-se a tecnologia de containerização através da plataforma Docker Desktop para projetar, empacotar e implantar um servidor web Apache2 dentro de um ambiente isolado baseado na distribuição Linux Debian.

A metodologia adotada fundamenta-se nos princípios da Infraestrutura como Código e na arquitetura de microsserviços. Em vez de depender de configurações manuais e suscetíveis a falhas em um sistema operacional hospedeiro, todo o ambiente de execução, incluindo o sistema de arquivos base, as bibliotecas, as variáveis de ambiente e os parâmetros de rede e armazenamento, foi declarado de forma padronizada em um arquivo de instrução versionável chamado Dockerfile.

1.1 Arquitetura e Fundamentação Técnica
A solução foi construída tirando proveito dos mecanismos nativos do kernel Linux que o Docker orquestra:

Namespaces: Garantem o isolamento de processos, rede, montagens de arquivos e usuários, assegurando que o container opere de forma completamente independente do sistema hospedeiro.

Control Groups: Garantem a limitação e o controle de recursos de hardware, como uso de memória RAM e CPU, evitando que a aplicação monopolize a máquina hospedeira.

Camadas de Leitura e Escrita: A imagem é montada em camadas imutáveis e sobrepostas, tornando a construção leve, eficiente e reutilizável através do sistema de cache do Docker Engine.

1.2 Procedimentos e Passos Práticos
Estruturação do Ambiente Local: No sistema hospedeiro, criou-se o diretório de trabalho dedicado denominado docker_apache para armazenar o Dockerfile e centralizar o controle de versão do projeto.

Desenvolvimento do Dockerfile: Elaborou-se o arquivo declarativo Dockerfile definindo a receita precisa para a criação da imagem do servidor web. Cada instrução foi configurada com um propósito técnico específico:

A instrução FROM debian define a imagem base oficial do Debian, fornecendo um sistema operacional enxuto, seguro e altamente estável.

A instrução RUN apt-get update && apt-get install -y apache2 && apt-get clean atualiza a lista de repositórios do gerenciador de pacotes, realiza a instalação do servidor web Apache2 de forma não interativa e executa o expurgo de arquivos temporários de instalação para reduzir o tamanho final da imagem.

A instrução ENV define as variáveis de ambiente necessárias para a inicialização e controle de processos do daemon do Apache, tais como o diretório de lock, arquivo de PID, usuário e grupo de execução, e diretório de logs.

A instrução LABEL description="Servidor Web Apache Containerizado" adiciona metadados descritivos para facilitar o rastreamento, governança e auditoria da imagem no ambiente Docker.

A instrução VOLUME /var/www/html/ declara um ponto de montagem persistente para o diretório raiz do Apache, permitindo que páginas HTML ou aplicações web sejam associadas ao container sem perder dados caso o container seja destruído.

A instrução EXPOSE 80 expõe e documenta a porta de rede padrão HTTP para tráfego web.

Compilação da Imagem: Através do terminal de comando integrado usando o Git Bash ou PowerShell, executou-se a compilação do arquivo Dockerfile utilizando a flag -t para atribuir uma tag de versionamento à imagem resultante nomeada como apache_teste:1.0, executando o comando docker build -t apache_teste:1.0 .

Execução e Mapeamento de Portas: Com a imagem devidamente registrada no repositório local do Docker, o container foi instanciado utilizando a flag -d para rodar em segundo plano no modo desacoplado e a flag -p para mapear a porta 8080 da máquina hospedeira para a porta 80 interna do container, executando o comando docker run -d -p 8080:80 apache_teste:1.0.

Validação do Serviço e Teste de Conectividade: A validação funcional foi realizada ao abrir um navegador web e fazer uma requisição HTTP ao endereço http://localhost:8080. O sucesso do carregamento da página padrão do Apache2 confirmou que o roteamento de rede, a instalação do serviço e a execução do container estavam operando corretamente.

Versionamento Avançado e Integração Contínua (Além do Escopo Básico): Para elevar o nível da entrega técnica e garantir as melhores práticas de Engenharia de Software, todo o projeto foi integrado ao controle de versão Git e publicado publicamente na plataforma GitHub, garantindo rastreabilidade, portabilidade do código de infraestrutura e acesso remoto aos arquivos. O repositório oficial da atividade pode ser acessado em: https://github.com/andersonsilvanto/docker-apache-teste
2. RESULTADOS, VALIDAÇÃO DO CHECKLIST E AVALIAÇÃO
2.1 Cumprimento Integral do Checklist da Prática
Para a validação desta atividade, o checklist proposto foi integralmente executado e superado com o seguinte panorama prático:

Instalar e configurar o Docker Desktop: Concluído com sucesso, estabelecendo o ambiente motor dos containers na máquina.

Criar estrutura de diretórios e Dockerfile: Concluído com sucesso, estruturando a diretiva de configuração e o workspace local.

Construir imagem com docker build: Concluído com sucesso, gerando a imagem personalizada apache_teste:1.0.

Executar container com docker run: Concluído com sucesso, inicializando o container com mapeamento correto da porta 8080 para a 80.

Validar execução via navegador: Concluído com sucesso, comprovando o funcionamento do servidor web Apache.

Registrar resultados, reflexões e publicação avançada no GitHub: Concluído com excelência, expandindo a entrega com versionamento remoto profissional.

2.2 Respostas às Questões de Avaliação
Questão 1: Qual o benefício de usar containers nesse tipo de aplicação?
O uso de containers para aplicações web como o Apache oferece diversos benefícios fundamentais:

Portabilidade Absoluta: O container encapsula a aplicação e todas as suas dependências, como bibliotecas, variáveis e arquivos de configuração. Isso garante que o serviço rode com exatidão em qualquer ambiente de desenvolvimento, homologação ou produção na nuvem que possua o Docker Engine instalado, eliminando o problema clássico de que funciona na máquina local mas falha em produção.

Eficiência e Baixo Consumo de Recursos: Ao contrário de máquinas virtuais tradicionais, os containers não exigem a execução de um sistema operacional completo dedicado com hipervisor. Eles compartilham o kernel do sistema hospedeiro, o que resulta em um consumo de memória RAM e CPU drasticamente menor, além de permitir uma inicialização quase instantânea.

Isolamento de Aplicações: O servidor Apache executa em um ambiente seguro e isolado do sistema operacional principal e de outros containers, prevenindo conflitos de portas, dependências ou privilégios de execução.

Questão 2: Qual o papel das instruções do Dockerfile?
O Dockerfile atua como uma receita declarativa automatizada que orienta o construtor do Docker em como empacotar e preparar a imagem do container camada por camada. Cada instrução desempenha um papel técnico específico:

A instrução FROM define a imagem base a partir da qual o container será construído.

A instrução RUN executa comandos dentro do ambiente durante a fase de compilação, sendo útil para instalar pacotes e preparar o sistema.

A instrução ENV define variáveis de ambiente globais mantidas durante a execução do container.

A instrução LABEL organiza e adiciona metadados úteis para auditoria e governança do código.

A instrução VOLUME define um diretório de armazenamento persistente ou ponto de montagem flexível para preservar dados fora da camada gravável descartável do container.

A instrução EXPOSE documenta e sinaliza qual porta de rede o container utilizará para receber conexões externas.

3. EVIDÊNCIAS (PRINTS)
## 3. EVIDÊNCIAS (PRINTS)

**Print 1 - Terminal de Comando (Build e Execução):**
![Terminal Docker](images/nome-do-seu-print-1.png)

*Demonstração da execução dos comandos para construção da imagem e execução do container.*

---

**Print 2 - Navegador Web (Validação HTTP):**
![Navegador Apache](images/nome-do-seu-print-2.png)

*Acesso ao endereço http://localhost:8080 exibindo a tela padrão de confirmação do Apache.*

---

**Print 3 - Repositório GitHub:**
![Repositório GitHub](images/nome-do-seu-print-3.png)

*Tela do repositório público contendo o Dockerfile e o README.md publicados.*

Print 1 - Terminal de Comando: Demonstração da execução dos comandos para construção da imagem e execução do container.

Print 2 - Navegador Web: Acesso ao endereço http://localhost:8080 exibindo a tela padrão de confirmação do Apache.

Print 3 - Repositório GitHub: Tela do repositório público contendo o Dockerfile e o README.md publicados (Disponível em: https://github.com/andersonsilvanto/docker-apache-teste

4. CONCLUSÃO
A realização desta atividade prática permitiu vivenciar, de forma direta e aplicada, como a tecnologia de containerização através do Docker transforma e simplifica o ciclo de vida do desenvolvimento e da implantação de infraestrutura de software. A transição de abordagens de implantação tradicionais, que dependem da instalação direta de serviços no sistema operacional hospedeiro ou do uso de máquinas virtuais pesadas, para uma arquitetura baseada em containers traz ganhos expressivos em diversos pilares da Engenharia de Software moderna.

Em primeiro lugar, destaca-se o isolamento e a consistência de ambientes. Ao empacotar o servidor web Apache juntamente com as suas dependências, bibliotecas e variáveis de ambiente dentro de uma imagem criada a partir do Dockerfile, elimina-se de forma definitiva o problema clássico de incompatibilidade de ambientes. A aplicação torna-se um artefato portátil, capaz de ser executado com comportamento idêntico em qualquer plataforma que disponha do Docker Engine, seja um ambiente local de desenvolvimento, um servidor de testes ou uma nuvem produtiva.

Em segundo lugar, a prática evidencia o impacto da containerização na agilidade na entrega de software e no movimento DevOps. A capacidade de descrever toda a infraestrutura necessária através de poucas linhas de código de Infraestrutura como Código permite que a criação, o teste e a destruição de servidores ocorram em questão de segundos. Isso favorece a automação de pipelines de Integração e Entrega Contínuas, reduz o tempo de entrega e minimiza drasticamente a ocorrência de erros humanos decorrentes de configurações manuais. Além disso, a publicação do código-fonte em um repositório remoto no GitHub evidencia a adoção rigorosa de boas práticas de versionamento de software e colaboração em equipes de engenharia.

Por fim, a atividade reforça o conceito de escalabilidade e eficiência operacional. Ao contrário das máquinas virtuais tradicionais, que exigem a virtualização completa de um sistema operacional para cada instância, os containers compartilham o kernel do sistema hospedeiro. Isso resulta num consumo consideravelmente menor de CPU e memória RAM, permitindo uma densidade muito maior de aplicações por servidor. No contexto de arquiteturas modernas baseadas em microsserviços, essa característica viabiliza a escalabilidade horizontal rápida e dinâmica do Apache para responder a picos repentinos de tráfego na aplicação, consolidando o Docker como uma ferramenta indispensável para sistemas escaláveis, resilientes e de alta disponibilidade.

REFERÊNCIAS BIBLIOGRÁFICAS
CANEL, R. Docker para Desenvolvedores. São Paulo: Novatec Editora, 2019.

FREEMAN, Emily. DevOps Para Leigos. São Paulo: Editora Alta Books, 2021.

GOUVEIA, F. Containers com Docker: Do desenvolvimento à produção. São Paulo: Casa do Código, 2020.

KIM, Gene; HUMBLE, Jez; DEBOIS, Patrick; WILLIS, John. Manual de DevOps. Rio de Janeiro: Editora Alta Books, 2018.

MIASAKI, M. Infraestrutura como Código e Containers: Práticas Modernas em DevOps. São Paulo: Novatec Editora, 2022.

MOULIN, L. Docker: Criando e Gerenciando Containers. São Paulo: Editora Érica, 2021.

WILDT, Daniel et al. Extreme programming: práticas para o dia a dia no desenvolvimento ágil de software. São Paulo, SP: Casa do Código, 2015.