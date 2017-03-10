---
title: "Editar e continuar (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "C/C++, Editar e continuar"
  - "depurando [C++], Editar e continuar"
  - "Editar e Continuar [C++]"
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Editar e continuar (Visual C++)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar Editar e continuar em projetos do Visual C\+\+. Consulte [Alterações de código suportadas \(C\+\+\)](../debugger/supported-code-changes-cpp.md) para obter informações sobre as limitações de editar e continuar.  
  
 Iniciando na atualização 1 do Visual Studio 2015, agora você pode usar Editar e continuar em aplicativos da Windows Store C\+\+ e DirectX, porque ele agora oferece suporte a **\/ZI** opção de compilador com **\/bigobj** alternar. Você também pode usar Editar e continuar com os binários compilados com o **\/FASTLINK** alternar.  
  
 Outros aprimoramentos de atualização 1 incluem uma caixa de diálogo Novo, cancelável espera e notificação quando um arquivo não suporta editar e continuar. Para obter mais informações sobre os aprimoramentos na atualização 1, consulte [melhorias para C\+\+ editar e continuar na atualização 1 do Visual Studio 2015](http://blogs.msdn.com/b/vcblog/archive/2015/11/30/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1.aspx).  
  
o [\/Zo \(melhorar a otimização de depuração\)](/visual-cpp/build/reference/zo-enhance-optimized-debugging) opção de compilador que foi introduzida no Visual Studio 2013 atualização 3 adiciona informações adicionais para arquivos. PDB \(símbolo\) para binários compilados sem o [\/Od \(desabilitar \(Depurar\)\)](http://msdn.microsoft.com/library/aafb762y.aspx) opção.  
  
**\/Zo** desabilita editar e continuar. Consulte [Como depurar o código otimizado](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a>Habilitar ou desabilitar o editar e continuar  
Você talvez queira desabilitar a invocação automática de editar e continuar, se você estiver fazendo edições ao código que você deseja não aplicado durante a sessão de depuração atual. Você também pode habilitar novamente automática editar e continuar.  
  
1.  No menu **Ferramentas**, selecione **Opções**.  
  
2.  No **opções** caixa de diálogo, selecione **depuração \/ geral**.  
  
3.  No **Editar e continuar** grupo, marque ou desmarque o **Habilitar nativo editar e continuar** caixa de seleção.  
  
Alterar essa configuração afeta todos os projetos que você trabalha. Você não precisa recriar seu aplicativo após alterar essa configuração. Você pode alterar a configuração, mesmo enquanto você está depurando. Se você criar seu aplicativo de linha de comando ou de um makefile, mas depurar no ambiente do Visual Studio, você ainda pode usar Editar e continuar se você definir o **\/ZI** opção.  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a>Como aplicar alterações de código explicitamente  
No Visual C\+\+, editar e continuar podem aplicar alterações de código de duas maneiras. Alterações de código podem ser aplicadas implicitamente, quando você escolhe um comando de execução, ou explicitamente, usando o **Aplicar alterações de código** comando.  
  
Quando você aplicar alterações de código explicitamente, o programa permanece no modo de interrupção – nenhuma execução ocorre.  
  
-   Para aplicar alterações de código explicitamente, sobre o **Depurar** menu, escolha **Aplicar alterações de código**.  
  
## <a name="BKMK_How_to_stop_code_changes"></a>Como parar alterações de código  
Enquanto o editar e continuar estiver no processo de aplicar alterações de código, você pode interromper a operação.  
  
Para parar de aplicar alterações de código:  
  
-   Sobre o **Depurar** menu, escolha **Parar de aplicar alterações de código**.  
  
Este item de menu é visível apenas quando as alterações de código estão sendo aplicadas.  
  
Se você escolher essa opção, nenhuma das alterações de código serão confirmadas.  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a>Como redefinir o ponto de execução  
Algumas alterações de código podem fazer com que o ponto de execução seja movido para um novo local quando editar e continuar aplica as alterações. Editar e continuar coloca o ponto de execução mais precisamente possível, mas os resultados podem não ser corretos em todos os casos.  
  
No Visual C\+\+, uma caixa de diálogo informa quando muda o ponto de execução. Você deve verificar se o local está correto antes de continuar a depuração. Se não estiver correto, use o **Definir próxima instrução** comando. Para obter mais informações, consulte [Definir próxima instrução a executar](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="BKMK_How_to_work_with_stale_code"></a>Como trabalhar com código obsoleto  
Em alguns casos, editar e continuar não podem aplicar alterações de código para o executável imediatamente, mas podem ser capaz de aplicar as alterações de código mais tarde, se você continuar a depuração. Isso acontece se você editar uma função que chama a função atual ou se você adicionar mais de 64 bytes de novas variáveis para uma função na pilha de chamadas  
  
Nesses casos, o depurador continua executando o código original até que as alterações podem ser aplicadas. O código obsoleto aparece como uma janela de arquivo temporário de origem em uma janela de origem separado, com um título, como `enc25.tmp`. A origem editada continuará aparecendo na janela de origem original. Se você tentar editar o código obsoleto, uma mensagem de aviso será exibida.  
  
## Consulte também  
[Alterações de código suportadas \(C\+\+\)](../debugger/supported-code-changes-cpp.md)