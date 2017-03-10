---
title: "Habilitar testes de IU codificado dos controles | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "mlearned"
manager: "douge"
---
# Habilitar testes de IU codificado dos controles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O controle pode mais ser facilmente testado se você implementa o suporte para a interface do usuário codificado que testa a estrutura.  Você pode adicionar níveis crescentes de suporte incremental.  Você pode iniciar a validação de suporte do registro e de repetição e a propriedade.  Você pode criar no para permitir que o construtor codificado de teste da interface do usuário confirme as propriedades personalizadas do seu controle, e fornece classes personalizadas para acessar essas propriedades de código gerado.  Você também pode ajudar o construtor codificado de teste da interface de usuário para capturar ações de uma maneira que seja mais perto da intenção da ação que está sendo registrada.  
  
 **Neste tópico:**  
  
1.  [Oferecer suporte à validação do registro e de repetição e a propriedade implementando a acessibilidade](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2.  [Oferecer suporte à validação da propriedade personalizada implementando um provedor de propriedade](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3.  [Oferecer suporte à geração de código implementando uma classe para acessar propriedades personalizadas](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4.  [Oferecer suporte a ações Intenção- reconhecem implementando um filtro de ação](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
 ![CUIT&#95;Full](../test/media/cuit_full.png "CUIT\_Full")  
  
##  <a name="recordandplayback"></a> Oferecer suporte à validação do registro e de repetição e a propriedade implementando a acessibilidade  
 O construtor codificado de teste da interface do usuário captura informações sobre os controles que encontrar durante uma gravação e gerencia o código para repetir sessão.  Se o controle não oferece suporte a acessibilidade, o construtor codificado de teste da interface do usuário detectará as ações \(como cliques do mouse\) que usam coordenadas de tela.  Quando o teste tiver sido executada, o código gerado emitirá os cliques do mouse nas mesmas coordenadas de tela.  Se o controle for exibida em um local diferente na tela quando o teste tiver sido executada, o código gerado não executará a ação no seu controle.  Isso pode resultar em falhas se o teste não tiver sido executada em diferentes configurações da tela, em ambientes diferentes, ou depois que houve mudanças no layout de interface do usuário.  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT\_RecordNoSupport")  
  
 Se você implementar a acessibilidade, entretanto, o construtor codificado de teste da interface do usuário usará o para capturar informações sobre o controle quando registrar um teste e gerar código.  Então, quando você executa o teste, o código gerado reproduzir os eventos em seu controle, mesmo se estiver em outro lugar na interface do usuário.  Os autores de teste também poderão criar afirmam usando as propriedades básicas do controle.  
  
 ![CUIT&#95;Record](../test/media/cuit_record.png "CUIT\_Record")  
  
### Para dar suporte ao registro e o reprodução, a validação da propriedade, e a navegação para um controle do windows forms  
 Implementar a acessibilidade para o controle de acordo com o seguinte procedimento, e explicado em detalhes em <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT&#95;Accessible](../test/media/cuit_accessible.png "CUIT\_Accessible")  
  
1.  Implementar uma classe que deriva de <xref:System.Windows.Forms.Control.ControlAccessibleObject>, e substituir a propriedade de <xref:System.Windows.Forms.Control.AccessibilityObject%2A> para retornar um objeto da sua classe.  
  
    ```c#  
    public partial class ChartControl : UserControl  
    {  
        // Overridden to return the custom AccessibleObject for the control.  
        protected override AccessibleObject CreateAccessibilityInstance()  
        {  
            return new ChartControlAccessibleObject(this);  
        }  
  
        // Inner class ChartControlAccessibleObject represents accessible information  
        // associated with the ChartControl and is used when recording tests.  
        public class ChartControlAccessibleObject : ControlAccessibleObject  
        {  
            ChartControl myControl;  
            public ChartControlAccessibleObject(ChartControl ctrl)  
                : base(ctrl)  
            {  
                myControl = ctrl;  
            }  
        }  
    }  
    ```  
  
2.  Substituir <xref:System.Windows.Forms.AccessibleObject.Role%2A>do objeto acessível, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> e propriedades e métodos de <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> .  
  
3.  Implementar outro objeto de acessibilidade para o controle filho e substituir a propriedade filho de <xref:System.Windows.Forms.Control.AccessibilityObject%2A> de controle para retornar que objeto de acessibilidade.  
  
4.  Substituir <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A>, e propriedades e métodos de <xref:System.Windows.Forms.AccessibleObject.Select%2A> do objeto filho de acessibilidade do controle.  
  
> [!NOTE]
>  O início deste tópico com o exemplo de acessibilidade em <xref:System.Windows.Forms.AccessibleObject> neste procedimento, e em seguida no que criam procedimentos restantes.  Se você quiser criar uma versão para trabalhar de exemplo de acessibilidade, crie um aplicativo de console e substitua o código em Program.cs com o código de exemplo.  Você precisará adicionar referências à acessibilidade, a System.Drawing, e o System.Windows.Forms.  Você deve alterar **Inserir Tipos Interop** para facilitar o uso como false para eliminar um aviso de compilação.  Você pode alterar o tipo de saída do projeto de aplicativo de console para o aplicativo do Windows de forma que uma janela do console não aparecem quando você executa o aplicativo.  
  
##  <a name="customproprties"></a> Oferecer suporte à validação da propriedade personalizada implementando um provedor de propriedade  
 Uma vez que você implementou o suporte básico para a validação do registro e de repetição e de propriedade, você pode tornar as propriedades personalizadas do seu controle teste codificados disponíveis da interface do usuário implementando um plug\-in de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> .  Por exemplo, o procedimento a seguir cria um provedor de propriedade que permite que os testes codificados da interface do usuário acessem a propriedade do estado dos controles filho de CurveLegend o controle de gráfico.  
  
 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png "CUIT\_CustomProps")  
  
### Para dar suporte à validação da propriedade personalizada  
 ![CUIT&#95;Props](../test/media/cuit_props.png "CUIT\_Props")  
  
1.  Substituir a propriedade de <xref:System.Windows.Forms.AccessibleObject.Description%2A> do objeto acessível da legenda da curva para passar valores de propriedade avançada na cadeia de caracteres de descrição, separadamente da descrição principal \(e se você estiver implementando várias propriedades\) por ponto\-e\-vírgula \(;\).  
  
    ```c#  
    public class CurveLegendAccessibleObject : AccessibleObject  
    {  
        // add the state property value to the description  
        public override string Description  
        {  
            get  
            {  
                // Add “;” and the state value to the end  
                // of the curve legend’s description  
                return "CurveLegend; " + State.ToString();  
            }  
        }  
    }  
    ```  
  
2.  Crie um pacote de extensão de teste da interface do usuário para o controle criando um projeto de biblioteca de classe e adicionar referências à acessibilidade, ao Microsoft.VisualStudio.TestTools.UITesting, ao Microsoft.VisualStudio.TestTools.UITest.Common, e o Microsoft.VisualStudio.TestTools.Extension.  Alterar **Inserir Tipos Interop** para facilitar o uso como false.  
  
3.  Adicione uma classe do provedor de propriedade que é derivada de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using Accessibility;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
    using Microsoft.VisualStudio.TestTools.UITest.Common;  
  
    namespace ChartControlExtensionPackage  
    {  
        public class ChartControlPropertyProvider : UITestPropertyProvider  
        {  
        }  
    }  
    ```  
  
4.  Implementar o provedor de propriedade colocando nomes de propriedade e descritores da propriedade em <xref:System.Collections.Generic.Dictionary%602>.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
5.  Substitua o <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> para indicar que o seu assembly fornece suporte controle\- específico para o seu controle e seus filhos.  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
6.  Substituir os métodos abstratos restantes de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
7.  Adicione uma classe do pacote de extensão que é derivada de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
8.  Defina o atributo de `UITestExtensionPackage` para o assembly.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
9. Na classe do pacote de extensão, substituição <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> para retornar a classe do provedor de propriedade quando um provedor de propriedade é solicitado.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
10. Substituir os métodos e as propriedades restantes abstratos de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
11. Criar seus binários e os copia a **%ProgramFiles%\\ Comuns \\ Microsoft shared \\ VSTT \\ 10,0 \\ UITestExtensionPackages**.  
  
> [!NOTE]
>  Este pacote de extensão será aplicada a qualquer controle que seja do tipo “texto”.  Se você estiver testando vários controles do mesmo tipo, você precisará dos testa e gerenciá\-los separadamente dos pacotes de extensão são implantados quando você registra os testes.  
  
##  <a name="codegeneration"></a> Oferecer suporte à geração de código implementando uma classe para acessar propriedades personalizadas  
 Quando o construtor codificado de teste da interface de usuário gerencie o código de uma gravação da sessão, use a classe de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> para acessar seus controles.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 Se você tiver implementado um provedor de propriedade para fornecer acesso a propriedades personalizadas do controle, você pode adicionar uma classe especializada usada para acessar essas propriedades de modo que o código gerado é simplificado.  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
### Para adicionar uma classe especializada para acessar seu controle  
 ![CUIT&#95;CodeGen](../test/media/cuit_codegen.png "CUIT\_CodeGen")  
  
1.  Implementar uma classe que é derivada de <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> e adicionar o tipo de controle à coleção de propriedades de pesquisa no construtor.  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
2.  Implementar as propriedades personalizadas do seu controle como propriedades da classe.  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
3.  Substitua o método de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> do provedor de propriedade para retornar o tipo da nova classe dos controles filho da legenda da curva.  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
4.  Substitua o método de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> do provedor de propriedade para retornar o tipo método de PropertyNames do novo das classes.  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
##  <a name="intentawareactions"></a> Oferecer suporte a ações Intenção\- reconhecem implementando um filtro de ação  
 Quando o Visual Studio registra um teste, captura cada evento do mouse no teclado.  No entanto, em alguns casos, a tentativa de ação pode ser perdidas na série de eventos do mouse no teclado.  Por exemplo, se seu controle oferece suporte ao recurso preenchimento automático, o mesmo conjunto de eventos do mouse no teclado pode resultar em um valor diferente quando o teste tiver sido executada em um ambiente diferente.  Você pode adicionar um plug\-in de filtro da ação que substituir a série de eventos de teclado e do mouse em com uma única ação.  Dessa forma, você pode substituir a série de eventos do mouse no teclado resultando na seleção de um valor com uma única ação que define o valor.  Para fazer isso protege teste codificados de interface do usuário das diferenças no preenchimento automático de um ambiente para outro.  
  
### Para oferecer suporte a ações intenção\- reconhecem  
 ![CUIT&#95;Actions](../test/media/cuit_actions.png "CUIT\_Actions")  
  
1.  Implementar uma classe de filtro de ação que é derivada de <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, substituindo as propriedades <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> e <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
2.  Substitua <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>.  O exemplo a realpces é uma ação clique duas vezes em uma única ação em.  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
3.  Adicionar o filtro de ação ao método de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> do pacote de extensão.  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
4.  Criar seus binários e %ProgramFiles%os copia \\ arquivos comuns \\ Microsoft shared \\ VSTT \\ 10,0 \\ UITestExtensionPackages.  
  
> [!NOTE]
>  O filtro de ação não depende da implementação de acessibilidade ou do provedor de propriedade.  
  
## Depurar seu provedor de propriedade ou filtro da ação  
 Seu provedor de propriedade e filtro da ação são implementados em um pacote de extensão que é carregado e a execução codificado pelo construtor de teste da interface do usuário em um processo separado de seu aplicativo.  
  
#### Para depurar seu provedor ou ação da propriedade filtrar  
  
1.  Compile a versão de depuração de sua cópia do pacote de extensão .dll o e dos arquivos .pdb %ProgramFiles%\\ arquivos comuns \\ Microsoft shared \\ VSTT \\ 10,0 \\ UITestExtensionPackages.  
  
2.  Execute o aplicativo \(não no depurador\).  
  
3.  Executar o construtor codificado de teste da interface do usuário.  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  Anexe o depurador ao processo de codedUITestBuilder.  
  
5.  Definir pontos de interrupção no código.  
  
6.  No construtor codificado de teste da interface do usuário, crie afirma para exercer seu provedor de propriedade, e as ações do registro exercer a ação filtros.  
  
## Recursos externos  
  
### Orientação  
 [Teste para entrega contínua com o Visual Studio 2012 – Capítulo 2: Teste de Unidade: Testando o Interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## Consulte também  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)