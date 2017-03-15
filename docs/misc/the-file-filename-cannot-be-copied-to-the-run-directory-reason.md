---
title: "O arquivo &#39;filename&#39; n&#227;o pode ser copiado para o diret&#243;rio de execu&#231;&#227;o. &lt; motivo &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_to_run_dir"
ms.assetid: 80474e62-7cef-48e9-a7c0-820345d5b591
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O arquivo &#39;filename&#39; n&#227;o pode ser copiado para o diret&#243;rio de execu&#231;&#227;o. &lt; motivo &gt;
Esse erro é exibido quando:  
  
-   Uma referência que tenha o `CopyLocal` \(consulte a janela de propriedades quando a referência é selecionada no Gerenciador de soluções\) definida como `true` não pôde ser copiado para o diretório do qual o projeto está sendo executado.  
  
-   Uma dependência de uma referência com um `CopyLocal` definida como `true` não pôde ser copiado para o diretório do qual o projeto está sendo executado.  
  
-   Qualquer outro arquivo que precisava ser copiado localmente não pode ser copiado para o diretório do qual o projeto está sendo executado.  
  
 Geralmente, o `reason` citado no final do erro mensagem informará que o arquivo está em uso por outro processo. É provável que o arquivo está bloqueado por algo em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Pode haver um problema associado à criação de projetos no mesmo diretório de saída. Nesse caso, crie os dois projetos a diretórios diferentes. Ao criar em diretórios diferentes, o sistema de projeto copia todos os assemblies dependentes no diretório de saída do projeto.  
  
 Adicionando a saída de qualquer projeto que você está trabalhando como um item de caixa de ferramentas fará com que os designers de gerenciado bloquear a referência.  
  
 O sistema do projeto não será capaz de atualizar o diretório de saída se a saída está sendo executado.  
  
 **Para corrigir este erro**  
  
-   Verifique o espaço em disco disponível do computador  
  
-   Verifique se você está atingindo o limite MAX\_PATH imposto pelo sistema de arquivos  
  
     A situação não impedirá que o projeto seja criada. No entanto, ele pode evitar que o projeto seja executado corretamente, porque esse aviso indica que uma cópia privada de um assembly referenciado não pôde ser atualizada corretamente. Embora possam parecer executar o projeto, você pode receber um tipo de carga de exceções ou outro comportamento inesperado durante a execução de alguns caminhos de código.  
  
## Consulte também  
 [NIB: Como: definir a propriedade Copy Local de uma referência](http://msdn.microsoft.com/pt-br/dfe2ba13-f27f-4356-a481-ea67d5acacbd)