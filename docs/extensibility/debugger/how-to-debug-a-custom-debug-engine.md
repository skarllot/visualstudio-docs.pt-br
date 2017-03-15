---
title: "Como: Depurar um mecanismo de depuração personalizado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 9
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
ms.openlocfilehash: 82f289f96644aa4572ffd8c490c14ad9312b44bb
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-debug-a-custom-debug-engine"></a>Como: Depurar um mecanismo de depuração personalizado
Um tipo de projeto inicia o mecanismo de depuração (DE) do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> Isso significa que o DE é iniciado sob o controle da instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controlar o tipo de projeto. No entanto, essa instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não pode depurar DE. A seguir está as etapas para permitir a depuração DE seu personalizado.  
  
> [!NOTE]
>  : No procedimento "Depuração um personalizado depurar mecanismo", você deve aguardar o DE iniciar antes que você pode anexar a ele. Se você colocar uma caixa de mensagem próximo ao início do seu DE aparece quando o DE é iniciado, você pode anexar nesse ponto e, em seguida, desmarque a caixa de mensagem para continuar. Dessa forma, você pode capturar todos os eventos DE.  
  
> [!WARNING]
>  Você deve ter a depuração remota instalados antes de tentar os procedimentos a seguir. Consulte [depuração remota](../../debugger/remote-debugging.md) para obter detalhes.  
  
### <a name="debugging-a-custom-debug-engine"></a>Depuração de um mecanismo de depuração personalizado  
  
1.  Iniciar msvsmon.exe, o Monitor de depuração remota.  
  
2.  Do **ferramentas** menu msvsmon.exe, selecione **opções** para abrir o **opções** caixa de diálogo.  
  
3.  Selecione a opção "sem autenticação" e clique em **Okey**.  
  
4.  Iniciar uma instância de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e abra o projeto DE personalizado.  
  
5.  Inicie uma segunda instância de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e abra o projeto personalizado que inicia DE (para o desenvolvimento, isso normalmente é no hive do registro experimental que é configurado quando VSIP está instalado).  
  
6.  Na segunda instância de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregar um arquivo de origem do projeto personalizado e iniciar o programa a ser depurado. Aguarde alguns instantes para permitir que o DE carregar ou aguarde até que um ponto de interrupção é atingido.  
  
7.  Na primeira instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (com seu projeto DE), selecione **anexar ao processo** do **depurar** menu.  
  
8.  No **anexar ao processo** caixa de diálogo, altere o **transporte** para **remoto (somente nativo sem autenticação)**.  
  
9. Alterar o **qualificador** para o nome do seu computador (Observação: há um histórico das entradas, por isso você precisa digitar esse nome apenas uma vez).  
  
10. No **processos disponíveis** , selecione a instância do seu DE que está em execução e clique no **Attach** botão.  
  
11. Após carregaram os símbolos no seu DE, coloca pontos de interrupção no seu código DE.  
  
12. Sempre que você para e reiniciar o processo de depuração, repita as etapas 6 a 10.  
  
### <a name="debugging-a-custom-project-type"></a>Depuração de um tipo de projeto personalizado  
  
1.  Iniciar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no hive do registro normal e carregar seu projeto digite projeto (isto é, a fonte ao tipo de projeto, não uma instanciação de seu tipo de projeto).  
  
2.  Abra as propriedades do projeto e vá para o **depurar** página. Para o **comando**, digite o caminho para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (por padrão, isso é *[unidade]*\Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Para o **argumentos de comando**, digite `/rootsuffix exp` para o hive do registro experimental (criado ao VSIP foi instalado).  
  
4.  Clique em **OK** para aceitar as alterações.  
  
5.  Inicie o tipo de projeto pressionando F5. Isso iniciará uma segunda instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  Neste ponto, você pode colocar pontos de interrupção no seu código de tipo de projeto.  
  
7.  Na segunda instância de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], carregar ou criar uma nova instância do seu tipo de projeto. Durante o carregamento ou a criação, os pontos de interrupção podem ser atingidos.  
  
8.  Depure o tipo de projeto.  
  
9. Se você escolher depurar o processo de inicialização DE, você pode executar as etapas no procedimento "Depuração um personalizado depurar mecanismo" anexar à sua DE após ele é iniciado. Isso dará a você três instâncias do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] em execução: um para a origem do tipo de projeto, um segundo para o tipo de projeto instanciado e um terceiro anexado ao seu DE.  
  
## <a name="see-also"></a>Consulte também  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
