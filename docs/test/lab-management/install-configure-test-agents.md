---
title: Instalar e configurar agentes de teste | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configure test agents, test lab
ms.assetid: EBAA2E04-A97A-4047-B739-8DBA7F2D5074
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: b7a186778434bc07c169c9f80879c8bc3607bcde
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="install-and-configure-test-agents"></a>Instalar e configurar agentes de teste

Para cenários de teste usando o Visual Studio e o Visual Studio Team Services ou o TFS (Team Foundation Server), você não precisará de um controlador de teste porque os Agents para Microsoft Visual Studio cuidam da orquestração se comunicando com o Team Services ou TFS. Por exemplo, você está executando testes contínuos com seus fluxos de trabalho de build e versão no Team Service ou TFS.

Se você precisar que seu agente de teste ou controlador de teste funcione com o TFS 2013, use os Agents para Microsoft Visual Studio 2013 Atualização 5 e configure o controlador de teste.

Além disso, considere se seria mais fácil [usar o Build ou Release Management em vez disso](use-build-or-rm-instead-of-lab-management.md).

## <a name="what-do-i-need"></a>Do que eu preciso?

**Onde obtenho o controlador de teste e os agentes de teste?**

* Se você estiver executando testes usando tarefas vNext do Build e desejar instalar agentes de um diretório local 

  * [Baixe os Agents para Microsoft Visual Studio 2015 RTM e Atualização 1](http://go.microsoft.com/fwlink/p/?LinkId=619266). 

  * [Baixe os Agents para Microsoft Visual Studio 2017 e o Visual Studio 2015 Atualização 2](https://www.visualstudio.com/downloads/download-visual-studio-vs), escolha **Ferramentas do Visual Studio 2015** e selecione **Agents para Visual Studio 2015** na barra de navegação esquerda.

* [Baixe os Agents para Microsoft Visual Studio 2013 Atualização 5](http://go.microsoft.com/fwlink/p/?LinkId=619264) se desejar executar:

  * Carregar testes usando computadores remotos locais.

  * Testes contínuos remotamente usando o Microsoft Test Manager ou MSTest e as configurações de teste para ambiente de laboratório.

  * Testes contínuos usando o TFS 2013.

Esses instaladores estão disponíveis como arquivos ISO (CD virtual) para a instalação fácil em máquinas virtuais. 

[Posso combinar versões do TFS, do Microsoft Test Manager, do controlador de teste e do agente de teste?](#MixedVersions)

**Quais requisitos do sistema preciso para instalar meu controlador de teste e os agentes de teste?**

| Item | Requisitos |
| ---- | ------------ |
| **Agente** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Versão 2, Service Pack 1 |
| **Controlador** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Versão 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>Perguntas e respostas

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>P: Posso combinar versões do TFS, do Microsoft Test Manager, do controlador de teste e do agente de teste?

R: Sim, aqui estão as combinações com suporte e compatíveis:

| TFS | Microsoft Test Manager com Central de Laboratório | Controlador | Agente |
| --- | -------------------------------------- | ---------- | ----- |
| 2015: atualizar do 2013 | 2013 | 2013 |2013 |
| 2015: nova instalação | 2013 | 2013 | 2013 |
| 2015: atualizar do 2013 ou nova instalação | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>P: O Agente de Teste 2015 dará suporte a todos os cenários com suporte pelo Test Controller e pelo Agente de Teste do Visual Studio 2013?

R: É recomendável que você use Agents para Visual Studio em todos os novos cenários de teste automatizado. Você pode usar a tarefa de Implantar Agentes de Teste em uma definição de build para baixar e instalar os agentes de teste em seu computador.
A tabela a seguir mostra os cenários com suporte pelo Agents para o Visual Studio 2013 e as alternativas para o TFS (Team Foundation Server) 2015 e TS (Team Services).

| Cenários com suporte pelo Agents para Visual Studio 2013 | Alternativa no TFS e TS |
| --- | --- |
| Fluxo de trabalho compilar-implantar-testar no Visual Studio | Os usuários podem usar uma [definição de build](https://www.visualstudio.com/team-services/continuous-integration/) (não um build XAML) para compilar, implantar e testar os cenários no TFS. |
| Teste de carga (teste de desempenho) usando computadores remotos locais | Use o Test Controller/Test Agents 2013 Atualização 5 para executar os testes de carga locais. [Mais informações](https://msdn.microsoft.com/en-us/library/ff400223.aspx). |
| Execução remota de testes automatizados do Microsoft Test Manager usando um ambiente de laboratório | Atualmente não há nenhuma alternativa para esse cenário. Recomendamos que você use a tarefa Executar Testes Funcionais nas definições de build e versão (não em um build XAML) para executar testes remotamente. |
| Desenvolvedores executando testes remotos no Visual Studio | Não há mais suporte. |

<!-- ENDSECTION -->

## <a name="see-also"></a>Consulte também

* [Configurando computadores e coletando informações de diagnóstico usando configurações de teste](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)

