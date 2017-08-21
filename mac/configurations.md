---
title: "Noções sobre configurações de build"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: e435418c0c77f1577e9db8ab35d76d6bd54f8447
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="understanding-build-configurations"></a>Noções sobre configurações de build

## <a name="project-build-configurations"></a>Configurações de build do projeto 

Projetos podem ter várias configurações e alternar entre elas permite produzir resultados diferentes no tempo de build. Por exemplo, ao usar uma Configuração de depuração, a saída incluirá símbolos de depuração, permitindo que o depurador resolva nomes de funções, parâmetros ou variáveis do rastreamento de pilha do aplicativo com falha. Usar uma configuração de depuração, no entanto, leva a um tamanho do arquivo inflado e isso não seria ideal para um aplicativo destinado à distribuição.

Cada plataforma terá configurações específicas para seu build. O desenvolvimento do Xamarin.Android sempre terá apenas uma configuração de Versão ou de Depuração. O Xamarin.iOS tem mais configurações. Projetos iOS mais recentes terão apenas configurações de depuração ou de versão, porém elas podem ser definidas para um dispositivo ou qualquer simulador instalado.

## <a name="solution-configurations"></a>Configurações da solução

Semelhante às configurações de projeto, as configurações da solução são usadas para criar configurações personalizadas para um projeto inteiro. Usando a guia **Mapeamentos de Configuração** no item **Build > Configurações**, você pode atribuir uma configuração de destino para cada item da solução, conforme ilustrado abaixo:


 ![Opções de mapeamento de configuração](media/projects-and-solutions-image3.png)

Para obter mais informações, consulte o vídeo do [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) de James Montemagno.

## <a name="run-configuration"></a>Configuração de execução

Nas versões anteriores do Xamarin Studio, era possível selecionar a opção para configurar um projeto como um **Projeto de Inicialização**, que é o projeto que é executado/depurado usando o comando run/debug global. Isso era indicado por uma face de tipos em negrito do nome do projeto no painel do projeto.

No Visual Studio para Mac, em vez de configurar um projeto de inicialização, é possível definir uma _configuração de execução_. As configurações de execução são apresentadas em uma lista suspensa na barra de ferramentas, ao lado de seletor de configuração de build, conforme ilustrado abaixo:

 ![Lista suspensa Configuração de execução](media/projects-and-solutions-image8.png)

Uma configuração de execução é um conjunto de opções com um nome e várias configurações que são definidas em um projeto para finalidades diferentes. Configurações de execução são definidas no nível de projeto e um padrão será criado automaticamente para cada projeto executável, embora seja possível adicionar tantos quantos forem necessários. Certos tipos de projeto geram configurações de execução adicionais automaticamente. Por exemplo, projetos watchOS podem gerar _Configurações de visão rápida e de notificação._ 
 
As configurações podem ser compartilhadas com outros desenvolvedores (nesse caso elas serão armazenadas no arquivo .csproj) ou mantidas localmente (nesse caso elas serão armazenados em um arquivo .user).

### <a name="android-run-configurations"></a>Configurações de execução do Android
 
Configurações de execução em projetos Android permitem que você especifique quais atividade, serviços ou receptores de difusão iniciar ao executar ou depurar o projeto. Você pode passar dados extras intencionais e definir sinalizadores de intenção para poder testar seus componentes em diferentes condições de inicialização.

Atividades além de `MainLauncher` precisarão ter `Exported=true` adicionado ao atributo Atividade para a depuração em um dispositivo físico ou ter filtros de Intenção definidos.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Exemplos de dados que podem ser incluídos em configurações de execução

A lista a seguir fornece alguns exemplos de dados que podem ser incluídos em configurações de execução:

* Projeto .NET regular
    * Aplicativo de inicialização alternativo
    * Argumentos iniciais
    * Diretório de trabalho
    * Variáveis de ambiente
    * Opções de tempo de execução mono (deve ser usado somente quando em execução no Mono)
* Projeto do Android
    * Ponto de entrada (atividade, serviço, receptor)
    * Dados e os argumentos de intenção
* Projeto do iOS
    * Modo (Normal, Fetch em segundo plano)
* Projeto de extensão de iOS
    * Aplicativo de inicialização: padrão ou personalizada
* Projeto do WatchKit
    * Modo (Visão rápida, Notificação)
    * Conteúdo da notificação

