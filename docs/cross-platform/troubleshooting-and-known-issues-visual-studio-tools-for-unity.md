---
title: "Solucionando problemas e problemas conhecidos (Visual Studio Tools for Unity) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "crdun"
manager: "crdun"
---
# Solucionando problemas e problemas conhecidos (Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nesta seção, você encontrará soluções para problemas comuns com o Visual Studio Tools para o Unity, descrições de problemas conhecidos e saiba como você pode ajudar a melhorar o Visual Studio Tools para o Unity pelo relatório de erros.  
  
## Solução de Problemas  
 Para resolver alguns problemas comuns com o Visual Studio Tools para o Unity, consulte as seções a seguir.  
  
### Migrando do UnityVS para Visual Studio Tools para o Unity  
 Se você estiver migrando de UnityVS para Visual Studio Tools para o Unity, você precisará gerar novas soluções do Visual Studio para seus projetos Unity.  
  
##### Para migrar seu projeto para Unity de 1,8 UnityVS para Visual Studio Tools para Unity 1.9  
  
1.  Exclua os arquivos de solução e projeto antigos do projeto Unity.  No diretório raiz do seu projeto para Unity, localize a. sln Visual Studio e. \* proj arquivos e excluí\-los todos.  
  
2.  Importe o Visual Studio Tools para o pacote do Unity para seu projeto para Unity.  Para obter informações sobre como importar o pacote VSTU, consulte Configurar o Visual Studio Tools para o Unity sobre o [Introdução](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) página.  
  
3.  Gere os novos arquivos de solução e projeto.  Se você quiser gerá\-las agora, no Editor do Unity, no menu principal, escolha **Visual Studio Tools**, **gerar arquivos de projeto**.  Caso contrário, você pode ignorar esta etapa se desejar; O Visual Studio Tools para o Unity gerará novos arquivos automaticamente quando você escolhe **Visual Studio Tools**, **aberto no Visual Studio**.  
  
### O Visual Studio não é possível carregar a solução Visual Studio Tools para o Unity criado  
 Para obter mais informações, consulte [a resposta a essa pergunta stackoverflow](http://stackoverflow.com/a/24035907/36702).  
  
### No Windows 8, o Visual Studio solicita para baixar a estrutura Unity de destino  
 UnityVS requer o.  NET framework 3.5, que não é instalado por padrão no Windows 8.  Para corrigir esse problema, siga as instruções para baixar e instalar o.  .NET framework 3.5.  
  
## Problemas conhecidos  
 Há problemas no Visual Studio Tools para o Unity que resultam de como o depurador interage com a versão mais antiga do Unity do compilador c\# conhecidos.  Estamos trabalhando para ajudar a corrigir esses problemas, mas você pode enfrentar os seguintes problemas nesse meio tempo.  
  
-   Quando estiver depurando, Unity, às vezes, a falha.  
  
-   Quando estiver depurando, Unity, às vezes, congela.  
  
-   Revisão dentro e fora de métodos às vezes se comporta incorretamente, especialmente em iteradores ou em instruções switch.  
  
## Erros de relatório  
 Ajude\-na melhorar a qualidade do Visual Studio Tools para o Unity, enviar relatórios de erros quando ocorrem falhas, congela ou outros erros.  Isso nos ajuda a investigar e corrigir problemas do Visual Studio Tools para o Unity.  Obrigado\!  
  
### Como relatar um erro quando o Visual Studio congela  
 Há relatórios Visual Studio às vezes congela durante a depuração com o Visual Studio Tools para o Unity, mas precisamos de mais dados para entender o problema.  Você pode nos ajudar a investigar, seguindo as etapas abaixo.  
  
##### Para relatar que o Visual Studio congela durante a depuração com o Visual Studio Tools para o Unity  
  
1.  Abra uma nova instância do Visual Studio.  
  
2.  Abra o diálogo Attach to Process.  Na nova instância do Visual Studio, no menu principal, escolha **Depurar**, **Attach to Process**.  
  
3.  Anexe o depurador à instância congelada do Visual Studio.  No **Attach to Process** caixa de diálogo, selecione a instância congelada do Visual Studio do **processos disponíveis** tabela e escolha o **anexar** botão.  
  
4.  Pause o depurador.  Na nova instância do Visual Studio, no menu principal, escolha **Depurar**, **Interromper tudo** ou simplesmente pressione **Ctrl \+ Alt \+ Break**.  
  
5.  Crie um despejo de thread.  Na janela de comando, digite o seguinte comando e pressione **Enter**.  
  
    ```powershell  
    Debug.ListCallStack /AllThreads /ShowExternalCode  
    ```  
  
     Talvez você precise fazer o **comando** janela visível primeiro.  No Visual Studio, no menu principal, escolha **exibição**, **outras janelas**, **janela comando**.  
  
6.  Por fim, envie o despejo de thread para [vstusp@microsoft.com](mailto:vstusp@microsoft.com), e uma descrição do que você estava fazendo quando o Visual Studio se tornou congelado.