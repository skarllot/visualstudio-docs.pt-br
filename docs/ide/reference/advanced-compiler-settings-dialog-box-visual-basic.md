---
title: "Caixa de diálogo Configurações Avançadas do Compilador (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4a23c5e37e380fc963c938d01cb2cfefeb91f21c
ms.lasthandoff: 02/22/2017

---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Caixa de diálogo Configurações de Compilador Avançadas (Visual Basic)
Use a caixa de diálogo **Configurações Avançadas do Compilador** do **Designer de Projeto** para especificar as propriedades avançadas de configuração de build do projeto. Essa caixa de diálogo aplica-se a somente projetos Visual Basic.  
  
### <a name="to-access-this-dialog-box"></a>Para acessar essa caixa de diálogo  
  
1.  No **Gerenciador de Soluções**, escolha um nó do projeto (não o nó **Solução**).  
  
2.  No menu **Projeto**, clique em **Propriedades**. Quando o **Designer de Projeto** for exibido, clique na guia **Compilar**.  
  
3.  Na [Página Compilar, Designer de Projeto (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), selecione a **Configuração** e a **Plataforma**. Nas configurações de build simplificadas, as listas **Configuração** e **Plataforma** não são exibidas. Para obter mais informações, consulte [Configurações de projeto de depuração e versão](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
4.  Clique em **Opções Avançadas de Compilação**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="optimizations"></a>Otimizações  
 As opções a seguir especificam otimizações que podem, em alguns casos, diminuir um arquivo de programa, fazer um programa executar mais rapidamente ou acelerar o processo de build.  
  
 **Remover verificações de estouro de inteiro**  
 Por padrão, essa caixa de seleção está desmarcada para habilitar a verificação de estouro de inteiro. Marque essa caixa de seleção para remover a verificação de estouro de inteiro. Se você marcar essa caixa de seleção, os cálculos de inteiro poderão ser mais rápidos. No entanto, se você remover a verificação de estouro e as capacidades de tipo de dados estourarem, resultados incorretos poderão ser armazenados sem gerar um erro.  
  
 Se as condições de estouro forem verificadas e uma operação de inteiro estourar, será gerada uma exceção <xref:System.OverflowException>. Se as condições de estouro não forem verificadas, estouros de operação de inteiro não gerarão uma exceção.  
  
 **Habilitar otimizações**  
 Por padrão, essa caixa de seleção está desmarcada para desabilitar otimizações do compilador. Marque essa caixa de seleção para habilitar otimizações do compilador. Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente. No entanto, uma vez que otimizações causam reorganização de código no arquivo de saída, as otimizações do compilador podem dificultar a depuração.  
  
 **Endereço básico de DLL**  
 Essa caixa de texto exibe o endereço básico de DLL padrão em formato hexadecimal. Em projetos de Biblioteca de Classes e Biblioteca de Controle, você pode usar essa caixa de texto para especificar o endereço básico a ser usado quando a DLL é criada.  
  
 **Gerar informações de depuração**  
 Selecione **Nenhum**, **Completo** ou **Somente pdb** na lista. **Nenhum** especifica que nenhuma informação de depuração deve ser gerada. **Total** especifica que informações completas de depuração devem ser geradas e **Somente pdb** especifica que apenas as informações de depuração de PDB devem ser geradas. Por padrão, essa opção é definida como **Completo**.  
  
## <a name="compilation-constants"></a>Constantes de Compilação  
 Constantes de compilação condicional têm um efeito semelhante ao de usar uma diretiva de pré-processador [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) em um arquivo de origem, exceto que constantes definidas são públicas e aplicam-se a todos os arquivos no projeto. Você pode usar constantes de compilação condicionais junto com a diretiva [#If... Then... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) para compilar os arquivos de origem condicionalmente. Consulte [Compilação Condicional](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).  
  
 **Definir a constante DEBUG**  
 Por padrão, essa caixa de seleção é marcada, especificando que uma constante DEBUG deve ser definida.  
  
 **Definir a constante TRACE**  
 Por padrão, essa caixa de seleção é marcada, especificando que uma constante TRACE deve ser definida.  
  
 **Constantes personalizadas**  
 Insira quaisquer constantes personalizadas para seu aplicativo nessa caixa de texto. As entradas devem ser delimitadas por vírgulas usando este formato: **Name1="Value1",Name2="Value2",Name3="Value3"**.  
  
## <a name="other-settings"></a>Outras configurações  
 **Gerar assemblies de serialização**  
 Essa configuração especifica se o compilador criará os assemblies de serialização XML. Os assemblies de serialização poderão melhorar o desempenho da inicialização de <xref:System.Xml.Serialization.XmlSerializer> se você tiver usado essa classe para serializar os tipos no código. Por padrão, essa opção é definida como **Automático**, que especifica que os assemblies de serialização serão gerados apenas se você tiver usado <xref:System.Xml.Serialization.XmlSerializer> para codificar tipos no código em XML. **Desativado** especifica que os assemblies de serialização nunca devem ser gerados, independentemente de o código usar <xref:System.Xml.Serialization.XmlSerializer>. **Ativado** especifica que os assemblies de serialização sempre devem ser gerados. Os assemblies de serialização são chamados `TypeName`.XmlSerializers.dll.  
  
## <a name="see-also"></a>Consulte também  
 [Página de Compilação, Designer de Projeto (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
