---
title: "Os comandos que devem ser executados após a instalação | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
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
ms.openlocfilehash: a3e966e1b160ed68f350a0fa0e77629edd7450be
ms.lasthandoff: 02/22/2017

---
# <a name="commands-that-must-be-run-after-installation"></a>Comandos que devem ser executados após a instalação
Se você implantar sua extensão por meio de um arquivo. msi, você deve executar `devenv /setup` como parte da instalação na ordem para o Visual Studio descobrir suas extensões.  
  
> [!NOTE]
>  As informações neste tópico se aplica a localização DevEnv com o Visual Studio 2008 e versões anteriores. Para obter informações sobre como descobrir DevEnv com versões posteriores do Visual Studio, consulte [requisitos do sistema de detecção de](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Localizando devenv.exe  
 Você pode localizar cada versão devenv.exe do registro valores [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gravam instaladores, usando a tabela de RegLocator e AppSearch tabela para armazenar os valores do registro como propriedades. Para obter mais informações, consulte [requisitos do sistema de detecção de](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Linhas da tabela RegLocator localizar devenv.exe de diferentes versões do Visual Studio  
  
|Signature_|Raiz|Chave|Nome|Tipo|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Linhas da tabela AppSearch para linhas correspondentes da tabela RegLocator  
  
|Propriedade|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Por exemplo, o Visual Studio installer grava o valor do registro de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** como **C:\VS2008\Common7\IDE\devenv.exe**, um caminho completo para o executável deve executar o instalador.  
  
 **Observação** porque a coluna de tipo RegLocator é 2, não é necessário especificar informações adicionais de versão na tabela de assinatura.  
  
## <a name="running-devenvexe"></a>Executando devenv.exe  
 Após a ação padrão é executada no instalador de AppSearch, cada propriedade na tabela AppSearch tem um valor apontando para o arquivo devenv.exe para a versão correspondente do Visual Studio. Se qualquer um dos valores do registro não estão presentes — porque essa versão do Visual Studio não está instalado, a propriedade especificada está definida como null.  
  
 Windows Installer oferece suporte à execução de um executável para que os pontos de uma propriedade por meio da ação personalizada digite 50. A ação personalizada deve incluir as opções de execução de script, msidbCustomActionTypeInScript (1024) e msidbCustomActionTypeCommit (512), para garantir que o VSPackage foi instalado com êxito antes de integrá-lo em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte a tabela CustomAction e opções de execução de no Script de ação personalizada.  
  
 Ações personalizadas do tipo 50 especificar a propriedade que contém o executável como o valor da coluna de origem e argumentos de linha de comando na coluna de destino.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Linhas da tabela CustomAction executar devenv.exe  
  
|Ação|Tipo|Origem|Destino|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Ações personalizadas devem ser criadas na tabela InstallExecuteSequence para agendá-los para execução durante a instalação. Use a propriedade correspondente em cada linha da coluna da condição para impedir que a ação personalizada seja executado se essa versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não está instalado no sistema.  
  
> [!NOTE]
>  `Null`propriedades são avaliadas como `False` quando usado em condições.  
  
 O valor da coluna de sequência para cada ação personalizada depende de outros valores de sequência no pacote do Windows Installer. Valores de sequência devem ser, de modo que as ações personalizadas devenv.exe executar como próximo possível imediatamente antes da ação padrão InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabela InstallExecuteSequence para agendar as ações personalizadas devenv.exe  
  
|Ação|Condição|Sequência|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Consulte também  
 [Instalando os VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
