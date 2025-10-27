Exercício para turma de Cloud
Cenário 01 - Modernização de aplicações

# Modernização da Aplicação de E-commerce "Connecta Vendas" com Docker e Kubernetes

## 1. Introdução

A "Connecta Vendas", uma empresa de varejo em plena expansão, busca modernizar sua principal plataforma de e-commerce para garantir escalabilidade, agilidade no desenvolvimento e otimização de custos.

Atualmente, a empresa opera em uma **infraestrutura híbrida**, com dois controladores de domínio Active Directory on-premises, responsáveis pela autenticação de funcionários e sistemas internos, e uma infraestrutura web hospedada no Microsoft Azure.

A equipe de Cloud foi incumbida de desenhar uma proposta e uma arquitetura para a adoção de **contêineres** e serviços de **Plataforma como Serviço (PaaS)**, visando a evolução da plataforma de e-commerce.

## 2. O Desafio

A aplicação de e-commerce da "Connecta Vendas" é uma aplicação monolítica desenvolvida em .NET Framework, com um banco de dados SQL Server. O modelo atual apresenta desafios significativos:

-   **Lentidão na Implementação de Novos Recursos:** O ciclo de desenvolvimento e implantação é lento e complexo, dificultando a resposta rápida às demandas do mercado.
-   **Dificuldade de Escalabilidade:** A escalabilidade da aplicação é limitada e, muitas vezes, exige provisionamento excessivo de recursos, gerando custos desnecessários.
-   **Dependência da Infraestrutura:** A aplicação está fortemente acoplada à infraestrutura subjacente, tornando a migração e a modernização um processo arriscado e demorado.
-   **Integração com Sistemas Legados:** A plataforma precisa se comunicar de forma segura com sistemas internos on-premises, que dependem da autenticação via Active Directory.

## 3. A Solução Proposta: Conteinerização e Orquestração em Ambiente Híbrido

A proposta central é modernizar a aplicação de e-commerce, quebrando-a em **microsserviços** e utilizando **Docker** para criar contêineres independentes para cada serviço. A orquestração desses contêineres será gerenciada pelo **Kubernetes**, implantado em um ambiente híbrido que aproveita tanto a infraestrutura on-premises quanto os recursos de nuvem do Azure.

## 4. Arquitetura de Referência

O desenho da arquitetura contempla os seguintes componentes:

-   **Docker:** Utilizado para empacotar cada microsserviço (ex: catálogo de produtos, carrinho de compras, checkout, etc.) em contêineres leves e portáteis. Isso garante a consistência do ambiente de desenvolvimento, teste e produção.

-   **Azure Kubernetes Service (AKS):** Cluster Kubernetes gerenciado no Azure, responsável por hospedar os microsserviços voltados para o cliente (front-end, catálogo, etc.). O AKS oferece escalabilidade automática, gerenciamento simplificado e integração nativa com outros serviços do Azure.

-   **Kubernetes On-Premises (via Azure Arc):** Para os microsserviços que necessitam de acesso direto e de baixa latência aos sistemas legados e ao Active Directory on-premises (ex: serviço de integração de pedidos com o ERP), será utilizado um cluster Kubernetes local. Este cluster será conectado e gerenciado de forma centralizada pelo Azure através do **Azure Arc**, que estende o plano de controle do Azure para a infraestrutura local.

-   **Integração com Active Directory:** A autenticação dos funcionários que acessam o painel administrativo continuará sendo gerenciada pelos controladores de domínio on-premises. Aplicações rodando no AKS poderão se integrar ao Active Directory para garantir uma experiência de logon único (SSO) e segura.

-   **Azure DevOps e CI/CD:** Será implementado um pipeline de integração e entrega contínua (CI/CD) utilizando o Azure DevOps. Este pipeline automatizará o processo de build, teste e implantação dos contêineres Docker nos clusters Kubernetes, agilizando a entrega de novas funcionalidades.

-   **Serviços PaaS do Azure:** A arquitetura se beneficiará de outros serviços PaaS do Azure, como:
    -   **Azure SQL Database:** Para garantir alta disponibilidade, escalabilidade e gerenciamento simplificado do banco de dados.
    -   **Azure Container Registry:** Um registro de contêiner privado para armazenar e gerenciar as imagens Docker.
    -   **Azure Monitor:** Para monitoramento centralizado da saúde e performance dos clusters e das aplicações.
    -   **Azure API Management:** Para gerenciar e proteger as APIs dos microsserviços.

## 5. Benefícios Esperados

-   **Agilidade e Inovação:** Adoção de uma arquitetura de microsserviços e pipelines de CI/CD permitirá o desenvolvimento e a implantação mais rápidos.
-   **Escalabilidade e Eficiência:** A capacidade de escalar microsserviços individualmente no AKS garantirá o uso otimizado de recursos.
-   **Portabilidade e Flexibilidade:** O uso de contêineres Docker e Kubernetes proporcionará a flexibilidade de executar as cargas de trabalho no ambiente mais adequado.
-   **Gestão Simplificada:** O Azure Arc permitirá a gestão centralizada dos clusters Kubernetes em ambiente híbrido.
-   **Segurança Aprimorada:** A integração com o Active Directory e o uso de serviços gerenciados do Azure fortalecerão a postura de segurança da aplicação.

## 6. Próximos Passos

A equipe de Cloud deverá, com base neste cenário, detalhar a proposta técnica, incluindo um cronograma de implementação, custos estimados e um plano de migração para a nova arquitetura. O desenho da arquitetura deverá seguir as melhores práticas do **Azure Well-Architected Framework** para garantir uma solução robusta, segura e otimizada.

Segurança Aprimorada: A integração com o Active Directory e o uso de serviços gerenciados do Azure fortalecerão a postura de segurança da aplicação.

6. Próximos Passos

A equipe de Cloud deverá, com base neste cenário, detalhar a proposta técnica, incluindo um cronograma de implementação, custos estimados e um plano de migração para a nova arquitetura. O desenho da arquitetura deverá seguir as melhores práticas do Azure Well-Architected Framework para garantir uma solução robusta, segura e otimizada.
