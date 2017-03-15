---
title: "Solução de problemas VSPackages | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 933b0177e3287717b2cfb900996b947db7034ee5
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-vspackages"></a>Os VSPackages de solução de problemas
A seguir estão os problemas comuns que você pode ter com o VSPackage e dicas para resolver os problemas.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Para solucionar problemas de um VSPackage que mantém o Visual Studio seja iniciado  
  
-   Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no modo de segurança.  
  
     Para iniciar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no modo de segurança, em um prompt de comando, digite **devenv.exe /safemode**.  
  
     Durante esse processo não VSPackages são carregados exceto os VSPackages são incluídos com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Para solucionar problemas de um VSPackage que não é carregado  
  
1.  Certifique-se de que você está usando a raiz do registro no qual o VSPackage é registrado para ser executado, geralmente a raiz do registro experimental.  
  
     Para obter mais informações, consulte [a instância Experimental](../extensibility/the-experimental-instance.md).  
  
2.  Se o VSPackage é direcionado para executar na raiz do registro experimental, certifique-se de que você está executando a versão experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Para executar a versão experimental, digite o seguinte em uma janela de comando: **devenv /rootsuffix exp**.  
  
3.  Verifique as entradas de registro de VSPackage.  
  
     Para obter mais informações, consulte [registrando VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) e [Gerenciando VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Abra o **saída** janela da instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que falha ao carregar o VSPackage. Informações sobre por que o VSPackage falha no carregamento podem ser exibidas na janela.  
  
    > [!NOTE]
    >  Se você estiver começando a versão experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inspecionar o ambiente de desenvolvimento integrado (IDE), o **saída** janela de ambas as versões.  
  
5.  Examine o log de atividades.  
  
     Para obter mais informações, consulte [como: usar o Log de atividade](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Para obter mais informações sobre as exceções geradas pelo IDE, clique em **exceções** sobre o **depurar** menu para habilitar as exceções. No **exceções** caixa de diálogo Selecionar os tipos de exceções que você deseja obter mais informações.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Para solucionar problemas de um VSPackage não registrar  
  
1.  Certifique-se de que o assembly de VSPackage reside em um local confiável. RegPkg não é possível registrar assemblies em um local não confiável ou parcialmente confiável, como um compartilhamento de rede na configuração de segurança do .net padrão. Embora um aviso é exibido sempre que um usuário cria um projeto em um local não confiável, a caixa de seleção "não mostrar esta mensagem novamente" pode evitar que esse aviso ocorra.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Para solucionar problemas de um comando que não é visível ou que gera um erro quando você clica em um comando  
  
1.  Mesclar os comandos de menu novo ou alterado e aqueles já no IDE, digitando o seguinte no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Prompt de comando: **devenv /rootsuffix Exp /Setup.**.  
  
2.  Verifique se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode encontrar UI.dll para o VSPackage.  
  
    1.  Localize o CLSID do VSPackage na seção de pacotes do registro:  
  
         Studio HKLM\Software\Microsoft\Visual\\*\<versão >*\packages.  
  
    2.  Verifique se o caminho fornecido pelo subchave SatelliteDll está correto.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Para solucionar problemas de um VSPackage que se comporta de forma inesperada  
  
1.  Definir pontos de interrupção no seu código.  
  
     Bons pontos de partida para depuração são o construtor e o método de inicialização. Você também pode definir pontos de interrupção na área que você deseja avaliar, como um comando de menu. Para habilitar pontos de interrupção, você deve executar sob o depurador.  
  
    1.  Sobre o **projeto** menu, clique em **propriedades**.  
  
    2.  Sobre o **páginas de propriedade** caixa de diálogo, selecione o **depurar** guia.  
  
    3.  No **argumentos de linha de comando** , digite o sufixo de raiz do ambiente de desenvolvimento que seus destinos de VSPackage. Por exemplo, para selecionar a compilação experimental, digite: **RootSuffix Exp**.  
  
    4.  Sobre o **depurar** menu, clique em **iniciar depuração** ou pressione F5.  
  
        > [!NOTE]
        >  Se você estiver depurando um projeto, criar ou carregar uma instância existente do seu projeto agora.  
  
2.  Use o log de atividades.  
  
     Rastreamento de comportamento de VSPackage gravando informações no log de atividade em pontos-chave. Essa técnica é especialmente útil quando você executa um VSPackage em um ambiente de varejo. Para obter mais informações, consulte [como: usar o Log de atividade](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Use símbolos públicos.  
  
     Para melhorar a legibilidade durante a depuração, você pode anexar símbolos no depurador.  
  
    1.  Do **Ferramentas/opções** menu, navegue até o **depuração/símbolos** caixa de diálogo.  
  
    2.  Adicione isso **símbolo local do arquivo (. PDB)**:  
  
         [http://MSDL.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Para melhorar o desempenho, especifique uma pasta de cache de símbolo, por exemplo:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Para solucionar problemas de um VSPackage ausente ou uma de suas dependências  
  
1.  Para código gerenciado, certifique-se de que os caminhos de referência estão corretos.  
  
    1.  Sobre o **projeto** menu, clique em **propriedades**.  
  
    2.  Selecione o **referências** guia de **páginas de propriedade** caixa de diálogo e verifique se todos os caminhos estão corretos. Como alternativa, você pode usar o **Pesquisador de objetos** para procurar os objetos referenciados.  
  
         Para código gerenciado, você pode usar o [Fuslogvw.exe (Assembly Binding Log Viewer)](http://msdn.microsoft.com/Library/e32fa443-0778-4cc3-bf36-5c8ea297d296) para exibir os detalhes de cargas de assembly com falha.  
  
2.  Para código não gerenciado, localize o CLSID do VSPackage no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nó de registro CLSID:  
  
     Studio HKLM\Software\Microsoft\Visual\\*\<versão >*\CLSID  
  
 Certifique-se de que a entrada InprocServer32 tem o caminho correto da dll VSPackage.  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)
