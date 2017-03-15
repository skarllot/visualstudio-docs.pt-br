---
title: Guia de Plug-ins de controle de origem de teste | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1c2a9af73e4236679b94a884ceae196ff75b3999
ms.lasthandoff: 02/22/2017

---
# <a name="test-guide-for-source-control-plug-ins"></a>Guia de teste para Plug-ins de controle de origem
Esta seção fornece orientações para testar o controle de origem plug-in com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. É fornecida uma visão geral abrangente das áreas mais comuns de testes, bem como algumas das áreas mais complexas que podem ser um problemas. Esta visão geral não pretende ser uma lista completa de casos de teste.  
  
> [!NOTE]
>  Algumas correções e aprimoramentos para o mais recente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pode revelar problemas com existente fonte plug-ins de controle que anteriormente não foram encontrados durante o uso de versões anteriores do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. É altamente recomendável que você teste o controle de origem existente plug-in para as áreas enumeradas nesta seção, mesmo que nenhuma alteração foi feita para o plug-in desde a versão anterior do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Preparação comuns  
 Uma máquina com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e plug-in de controle de origem destino instalado, é necessário. Um segundo computador configurado da mesma forma pode ser usado para algumas do aberto a partir de testes de controle de origem.  
  
## <a name="definition-of-terms"></a>Definições de termos  
 Para fins deste guia de teste, use as seguintes definições de termos:  
  
 Projeto de cliente  
 Tipo disponível em qualquer projeto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que oferece suporte à integração de controle de origem (por exemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ou [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Projeto da Web  
 Há quatro tipos de projetos da Web: sistema de arquivos, IIS Local, Sites remotos e FTP.  
  
-   Projetos de sistema de arquivos são criados em um caminho local, mas eles não exigem o Internet Information Services (IIS) a ser instalado como elas são acessadas internamente por meio de um caminho UNC e podem ser colocadas sob controle de origem de dentro do IDE, bem como projetos de cliente.  
  
-   Projetos de IIS locais funcionam com o IIS instalado no mesmo computador e é acessado com uma URL apontando para o computador local.  
  
-   Projetos de Sites remotos também são criados em dos serviços IIS, mas eles são colocados sob controle de origem no computador do servidor do IIS e não de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
-   Projetos FTP são acessados por meio de um servidor FTP remoto, mas eles não podem ser colocados sob controle de origem.  
  
 Inscrição  
 Outro termo para a solução ou projeto sob controle de origem.  
  
 Armazenamento de versão  
 O banco de dados que está sendo acessado por meio da API de plug-in de controle de origem.  
  
## <a name="test-areas-covered-in-this-section"></a>Áreas de teste abordadas nesta seção  
  
-   [Área de teste 1: Adicionar / Abrir do controle de origem](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Caso 1a: Adicionar solução ao controle de origem  
  
    -   Caso 1b: Abrir solução do controle de origem  
  
    -   Caso 1C: Adicionar solução do controle de origem  
  
-   [Área de teste 2: Obter do controle de origem](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Área de teste 3: Check-Out / desfazer check-out](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Caso 3: Check-Out / desfazer check-out  
  
    -   Caso 3a: Check-Out  
  
    -   Caso 3b: desconectado check-out  
  
    -   Caso 3C: Editar consulta/salvar (QEQS)  
  
    -   Caso 3d: Check-out silencioso  
  
    -   Caso 3e: desfazer check-out  
  
-   [Área de teste 4: Fazer Check-In](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Caso 4a: modificou itens  
  
    -   Caso 4b: adicionando arquivos  
  
    -   Caso c 4: Adicionando projetos  
  
-   [Área de teste 5: Alterar controle de origem](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Caso 5a: associar  
  
    -   Caso 5b: desvincular  
  
    -   Caso 5c: Reassociar  
  
-   [Testar área 6: excluir](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Testar área 7: compartilhamento](../../extensibility/internals/test-area-7-share.md)  
  
-   [Teste área 8: Alternância de plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Caso 8a: alterações automáticas  
  
    -   Caso 8b: alteração de solução  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md)
