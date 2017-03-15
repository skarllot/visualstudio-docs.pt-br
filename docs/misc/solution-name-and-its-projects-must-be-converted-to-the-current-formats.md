---
title: "Solu&#231;&#227;o &lt; nome &gt; e seus projetos devem ser convertidos nos formatos atuais. | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.querymigratesolution"
ms.assetid: 1ecb09ab-1283-4ba5-874c-f675905a3b7b
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Solu&#231;&#227;o &lt; nome &gt; e seus projetos devem ser convertidos nos formatos atuais.
Você abriu uma solução que foi criada em uma versão anterior do Visual Studio. Arquivos de solução e projeto devem ser convertidos para formatos atuais antes de uma solução pode ser aberta e editada na versão do Visual Studio instaladas no seu computador. Você pode escolher se deseja ou não converter a solução agora. As conversões de formato não podem ser desfeitas.  
  
> [!CAUTION]
>  Se a solução é armazenada no controle do código fonte e você pretende verificar a solução convertida, verifique primeiro se outras soluções compartilham qualquer um de seus projetos. Não verifica em uma solução que inclui projetos convertidos que ainda estão sendo usados em outras soluções não convertidas. Isso será quebrar as dependências dentro dessas soluções e impedir que eles sejam abrindo ou criando corretamente.  
  
 Talvez você queira fazer cópias de backup de seus arquivos de solução e projeto antes de convertê\-los.  
  
> [!NOTE]
>  Como soluções do Visual Studio são convertidas, os arquivos da solução anterior são marcados com a extensão de arquivo ". old" e salvos em seu diretório de solução de nível superior. Como determinados tipos de projeto são convertidos, por exemplo projetos do Visual C\+\+, os arquivos de projeto anterior são marcados com a extensão de arquivo ". old" da mesma forma e salvo no diretório do projeto.  
  
 Projetos somente leitura não são convertidos. Esses projetos podem ser convertidos somente pelos usuários que têm permissão para editá\-los. Antes de um projeto pode ser usado em uma solução convertida, seus arquivos de projeto devem ser convertidos para formatos atuais. Após a conversão uma solução ou qualquer um de seus projetos, você pode não editar, compilar ou executar a solução em versões anteriores do Visual Studio.  
  
### Para responder a esta mensagem  
  
1.  Selecione **Sim** ou **não**.  
  
    -   **Sim** \-o arquivo de solução e arquivos para seus projetos editáveis são convertidos nos formatos usados pela versão do Visual Studio instaladas no seu computador. Se a solução convertida armazenada sob controle do código fonte, é extraído em sua unidade local e aberto para edição.  
  
    -   **Não** \-a solução e seus projetos não são convertidos, não são verificados no controle do código fonte e não a abra.  
  
 Se você fizer parte de uma equipe de desenvolvimento, qualquer pessoa que está trabalhando em uma solução deve ter a mesma versão do Visual Studio instalado em suas máquinas locais. Para garantir que as soluções e projetos permanecem acessíveis, se comunicam regularmente com sua equipe.  
  
## Consulte também  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/pt-br/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compilando aplicativos no Visual Studio](../ide/compiling-and-building-in-visual-studio.md)