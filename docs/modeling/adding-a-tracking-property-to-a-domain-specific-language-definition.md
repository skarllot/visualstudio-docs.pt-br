---
title: "Adicionar uma propriedade de controle a uma definição de linguagem específica do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 22
author: alancameronwills
ms.author: awills
manager: douge
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ef5f86cb3b41af6cc9e7432cdbfb7365471320b8
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Adicionando uma propriedade de acompanhamento a uma definição de linguagem específica do domínio
Este passo a passo mostra como adicionar uma propriedade de controle a um modelo de domínio.  
  
 Um *controle domínio* é uma propriedade que pode ser atualizada pelo usuário, mas que tem um valor padrão é calculado usando os valores de outras propriedades do domínio ou elementos.  
  
 Por exemplo, nas ferramentas de linguagem específica de domínio (ferramentas de DSL), o nome de exibição a propriedade de uma classe de domínio tem um valor padrão é calculado usando o nome da classe de domínio, mas um usuário pode alterar o valor em tempo de design ou redefini-lo para o valor calculado.  
  
 Este passo a passo, você criará uma linguagem específica de domínio (DSL) que tem um Namespace de propriedade que tem um valor padrão com base na propriedade de Namespace padrão do modelo de controle. Para obter mais informações sobre propriedades de controle, consulte [definindo propriedades de controle](http://msdn.microsoft.com/en-us/0538b0e4-6221-4e7d-911a-b92cd622f0be).  
  
-   O suporte a ferramentas de DSL descritores de propriedade de rastreamento. No entanto, o designer DSL não pode ser usado para adicionar uma propriedade de controle a um idioma. Portanto, você deve adicionar código personalizado para definir e implementar a propriedade de controle.  
  
 Uma propriedade de controle tem dois estados: controle e atualizada pelo usuário. Propriedades de controle têm os seguintes recursos:  
  
-   Quando estiver no estado de controle, o valor da propriedade de controle é calculado e o valor é atualizado como outras propriedades na alteração do modelo.  
  
-   Quando estiver sendo atualizado pelo estado do usuário, o valor da propriedade de controle retém o valor para o qual o usuário última definir a propriedade.  
  
-   No **propriedades** janela, o **redefinir** comando para a propriedade de rastreamento é habilitada apenas quando a propriedade é em atualizado pelo estado do usuário. O **redefinir** comando define a propriedade de controle de estado do controle.  
  
-   No **propriedades** janela, quando a propriedade de controle está no estado de controle, seu valor é exibida em uma fonte regular.  
  
-   No **propriedades** janela, quando a propriedade de controle está no atualizado pelo estado do usuário, seu valor é exibido em uma fonte em negrito.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Antes de começar este passo a passo, você deve primeiro instalar esses componentes:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>Criando o projeto DSL  
 Crie o projeto para sua linguagem específica de domínio.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Crie um projeto do Designer de linguagem específica de domínio. Nomeie-o `TrackingPropertyDSL`.  
  
2.  No **Assistente de Designer de linguagem específica de domínio**, defina as seguintes opções:  
  
    1.  Selecione o **MinimalLanguage** modelo.  
  
    2.  Use o nome padrão para a linguagem específica de domínio, `TrackingPropertyDSL`.  
  
    3.  Definir a extensão para arquivos de modelo para `trackingPropertyDsl`.  
  
    4.  Use o ícone de modelo padrão para os arquivos de modelo.  
  
    5.  Defina o nome do produto `Product Name`.  
  
    6.  Defina o nome da empresa para `Company Name`.  
  
    7.  Use o valor padrão para o namespace raiz para projetos na solução, `CompanyName.ProductName.TrackingPropertyDSL`.  
  
    8.  Permitir que o assistente criar um arquivo de chave de nome forte para seus assemblies.  
  
    9. Examine os detalhes da solução e, em seguida, clique em **concluir** para criar o projeto de definição de DSL.  
  
## <a name="customizing-the-default-dsl-definition"></a>Personalizando a definição de DSL padrão  
 Nesta seção, você deve personalizar a definição de DSL para conter os seguintes itens:  
  
-   Um Namespace de propriedade para cada elemento do modelo de controle.  
  
-   Uma propriedade booleana IsNamespaceTracking para cada elemento do modelo. Essa propriedade indica se a propriedade de controle está no estado de controle ou no atualizado pelo estado do usuário.  
  
-   Uma propriedade de Namespace padrão para o modelo. Essa propriedade será usada para calcular o valor padrão para o Namespace de propriedade de controle.  
  
-   Uma propriedade CustomElements calculado para o modelo. Essa propriedade indicará a proporção dos elementos que têm um espaço para nome personalizado.  
  
#### <a name="to-add-the-domain-properties"></a>Para adicionar as propriedades do domínio  
  
1.  No designer de DSL, com o botão direito do **ExampleModel** classe de domínio, aponte para **adicionar**e, em seguida, clique em **DomainProperty**.  
  
    1.  Nomeie a nova propriedade `DefaultNamespace`.  
  
    2.  No **propriedades** janela para a nova propriedade, defina **valor padrão** para `DefaultNamespace`e defina **tipo** para **cadeia de caracteres**.  
  
2.  Para o **ExampleModel** domínio classe, adicione uma propriedade de domínio chamada `CustomElements`.  
  
     No **propriedades** janela para a nova propriedade, defina **tipo** para **calculado**.  
  
3.  Para o **ExampleElement** domínio classe, adicione uma propriedade de domínio chamada `Namespace`.  
  
     No **propriedades** janela para a nova propriedade, defina **é navegável** para **False**e defina **tipo** para **CustomStorage **.  
  
4.  Para o **ExampleElement** domínio classe, adicione uma propriedade de domínio chamada `IsNamespaceTracking`.  
  
     No **propriedades** janela para a nova propriedade, defina **é navegável** para **False**, defina **valor padrão** para `true`e defina **Tipo** para **booliano**.  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Para atualizar os detalhes DSL e elementos de diagrama  
  
1.  No designer de DSL, com o botão direito do **ExampleShape** forma de geometria, aponte para **adicionar**e, em seguida, clique em **decorador de texto**.  
  
    1.  Nomeie o novo decorador de texto `NamespaceDecorator`.  
  
    2.  No **propriedades** janela para o decorador de texto, defina **posição** para **InnerBottomLeft**.  
  
2.  No designer de DSL, selecione a linha que conecta o **ExampleElement** de classe para o **ExampleShape** forma.  
  
    1.  No **DSL detalhes** janela, selecione o **decorador mapas** guia.  
  
    2.  No **decoradores** lista, selecione **NamespaceDecorator**, marque sua caixa de seleção e, em seguida, o **exibir a propriedade** lista, selecione **Namespace**.  
  
3.  Em **DSL Explorer**, expanda o **Classes de domínio** pasta, com o botão direito do **ExampleElement** nó e, em seguida, clique **adicionar novo domínio descritor de tipo**.  
  
    1.  Expanda o **ExampleElement** nó e selecione o **descritor de tipo personalizado (descritor de tipo de domínio)** nó.  
  
    2.  No **propriedades** janela para o descritor de tipo de domínio, defina **personalizado codificado** para **True**.  
  
4.  Em **DSL Explorer**, selecione o **o comportamento de serialização Xml** nó.  
  
    1.  No **propriedades** janela, defina **personalizado Post carga** para **True**.  
  
## <a name="transforming-templates"></a>Transformando modelos  
 Agora que você definiu as propriedades e classes de domínio para seu DSL, verifique se a definição de DSL pode ser transformada corretamente para gerar novamente o código para seu projeto.  
  
#### <a name="to-transform-the-text-templates"></a>Transformar modelos de texto  
  
1.  Sobre o **Solution Explorer** barra de ferramentas, clique em **transformar todos os modelos de**.  
  
2.  O sistema gera novamente o código para a solução e salva DslDefinition.dsl. Para obter informações sobre o formato XML de arquivos de definição, consulte [o arquivo DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).  
  
## <a name="creating-files-for-custom-code"></a>Criando arquivos de código personalizado  
 Quando você transforma todos os modelos, o sistema gera o código-fonte que define a linguagem específica de domínio nos projetos Dsl e DslPackage. Para que você possa evitar interferir com o texto gerado, escreva seu código personalizado em arquivos que são diferentes dos arquivos de código gerado.  
  
 Você deve fornecer o código para manter o valor e o estado de sua propriedade de controle. Para ajudá-lo a distinguir seu código personalizado do código gerado e para evitar conflitos de nomenclatura de arquivo, coloque os arquivos de código personalizado em uma subpasta separada.  
  
#### <a name="to-create-the-code-files"></a>Para criar os arquivos de código  
  
1.  Em **Solution Explorer**, com o botão direito do **DSL** de projeto, aponte para **adicionar**e, em seguida, clique em **nova pasta**. Nomeie a nova pasta `CustomCode`.  
  
2.  Clique em novo **CustomCode** pasta, aponte para **adicionar**e, em seguida, clique em **Novo Item**.  
  
3.  Selecione o **arquivo de código** modelo, defina o **nome** para `NamespaceTrackingProperty.cs`e, em seguida, clique em **Okey**.  
  
     O arquivo NamespaceTrackingProperty.cs é criado e aberto para edição.  
  
4.  Na pasta, crie os seguintes arquivos de código: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, e `TypeDescriptor.cs`.  
  
5.  No **DslPackage** de projeto, crie também um `CustomCode` pasta e adicione a ele um `Package.cs` arquivo de código.  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>Adicionando Classes auxiliares para dar suporte a propriedades de controle  
 Para o arquivo HelperClasses.cs, adicione o `TrackingHelper` e `CriticalException` classes da seguinte maneira. Você fará referência a essas classes este passo a passo.  
  
#### <a name="to-add-the-helper-classes"></a>Para adicionar as classes auxiliares  
  
1.  Adicione o seguinte código ao arquivo HelperClasses.cs.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        internal static class TrackingHelper  
        {  
            /// <summary>Notify each model element in a collection that a tracked  
            /// property has changed.</summary>  
            /// <param name="store">The store for the model.</param>  
            /// <param name="collection">The collection of model elements that  
            /// contain the tracking property.</param>  
            /// <param name="propertyId">The ID of the tracking property.</param>  
            /// <param name="trackingPropertyId">The ID of the property that  
            /// indicates whether the tracking property is tracking.</param>  
            internal static void UpdateTrackingCollectionProperty(  
                Store store,  
                IEnumerable collection,  
                Guid propertyId,  
                Guid trackingPropertyId)  
            {  
                DomainPropertyInfo propInfo =  
                    store.DomainDataDirectory.GetDomainProperty(propertyId);  
  
                DomainPropertyInfo trackingPropInfo =  
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);  
  
                Debug.Assert(propInfo != null);  
                Debug.Assert(trackingPropInfo != null);  
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),  
                    "Tracking property not specified as a boolean");  
  
                foreach (ModelElement element in collection)  
                {  
                    // If the tracking property is currently tracking, then notify  
                    // it that the tracked property has changed.  
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);  
                    if (isTracking)  
                    {  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
            }  
        }  
  
        /// <summary>Helper class to flag critical exceptions from ones that are  
        /// safe to ignore.</summary>  
        internal static class CriticalException  
        {  
            /// <summary>Gets whether an exception is critical and can not be  
            /// ignored.</summary>  
            /// <param name="ex">The exception to check.</param>  
            /// <returns>True if the exception is critical.</returns>  
            internal static bool IsCriticalException(Exception ex)  
            {  
                if (ex is NullReferenceException  
                    || ex is StackOverflowException  
                    || ex is OutOfMemoryException  
                    || ex is System.Threading.ThreadAbortException)  
                    return true;  
  
                if (ex.InnerException != null)  
                    return IsCriticalException(ex.InnerException);  
  
                return false;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Adicionando código personalizado para o descritor de tipo personalizado  
 Implementar o `GetCustomProperties` método para o descritor de tipo para o `ExampleModel` classe de domínio.  
  
> [!NOTE]
>  O código que as ferramentas de DSL gerar para o descritor de tipo personalizado de `ExampleModel` chamadas `GetCustomProperties`; no entanto, as ferramentas de DSL não gerar um código que implementa o método.  
  
 Definir este método cria o rastreamento de descritor de propriedade para o Namespace de propriedade de controle. Além disso, fornecer atributos para a propriedade de controle permite que o **propriedades** janela para exibir a propriedade corretamente.  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Para modificar o descritor de tipo para a classe de domínio ExampleModel  
  
1.  Adicione o seguinte código ao arquivo TypeDescriptor.cs.  
  
    ```csharp  
    using System;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the custom type descriptor for the ExampleElement domain class, add  
        // the GetCustomProperties method.  
        public partial class ExampleElementTypeDescriptor  
        {  
            /// <summary>Returns the property descriptors for the described  
            /// ExampleElement domain class.</summary>  
            /// <remarks>This method adds the tracking property descriptor.  
            /// </remarks>  
            private PropertyDescriptorCollection GetCustomProperties(  
                Attribute[] attributes)  
            {  
                // Get the default property descriptors from the base class  
                PropertyDescriptorCollection propertyDescriptors =  
                    base.GetProperties(attributes);  
  
                // Get a reference to the model element that is being described.  
                ExampleElement source = this.ModelElement as ExampleElement;  
  
                //Add the descriptor for the tracking property.  
                if (source != null)  
                {  
                    DomainPropertyInfo domainProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.NamespaceDomainPropertyId);  
  
                    DomainPropertyInfo trackingProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);  
  
                    // Define attributes for the tracking property so that the  
                    // Properties window displays the property correctly.  
                    Attribute[] attr = new Attribute[] {  
                        new DisplayNameAttribute("Element Namespace"),  
                        new DescriptionAttribute("The namespace of the element."),  
                        new CategoryAttribute("Tracking Properties"),  
                    };  
  
                    propertyDescriptors.Add(new TrackingPropertyDescriptor(  
                        source, domainProperty, trackingProperty, attr));  
                }  
  
                // Return the property descriptors for this element  
                return propertyDescriptors;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-package"></a>Adicionando código personalizado para o pacote  
 O código gerado define um provedor de descrição de tipo para a classe de domínio ExampleElement; No entanto, você deve adicionar código para instruir o DSL para usar esse provedor de descrição de tipo.  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Para atualizar o pacote DSL para usar o descritor de tipo personalizado  
  
1.  Adicione o seguinte código ao arquivo Package.cs.  
  
    ```csharp  
    using System.ComponentModel;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // Override the default Initialize method.  
        internal sealed partial class TrackingPropertyDSLPackage  
        {  
            protected override void Initialize()  
            {  
                // Add the custom type descriptor for the ExampleElement type.  
                TypeDescriptor.AddProvider(  
                    new ExampleElementTypeDescriptionProvider(),  
                    typeof(ExampleElement));  
  
                base.Initialize();  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-model"></a>Adicionando código personalizado para o modelo  
 Implementar o `GetCustomElementsValue` método para o `ExampleModel` classe de domínio.  
  
> [!NOTE]
>  O código que as ferramentas de DSL gerar para `ExampleModel` chamadas `GetCustomElementsValue`; no entanto, as ferramentas de DSL não gerar um código que implementa o método.  
  
 Definindo o `GetCustomElementsValue` método fornece a lógica para a propriedade CustomElements calculado de `ExampleModel`. Esse método conta o número de `ExampleElement` classes de domínio que têm um Namespace de propriedade que tem um valor atualizado de usuário e retorna uma cadeia de caracteres que representa essa contagem como uma proporção dos elementos total no modelo de controle.  
  
 Além disso, adicione um `OnDefaultNamespaceChanged` método `ExampleModel`e substituir o `OnValueChanged` método do `DefaultNamespacePropertyHandler` aninhados a classe de `ExampleModel` chamar `OnDefaultNamespaceChanged`.  
  
 Como a propriedade DefaultNamespace é usada para calcular o Namespace controle de propriedade, `ExampleModel` deve notificar todos `ExampleElement` classes de domínio que o valor de DefaultNamespace foi alterado.  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Para modificar o manipulador de propriedade para a propriedade controlada  
  
1.  Adicione o seguinte código ao arquivo ExampleModel.cs.  
  
    ```csharp  
    using System.Linq;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        public partial class ExampleModel  
        {  
            public string GetCustomElementsValue()  
            {  
                if (this.Elements.Count == 0) return "0/0";  
  
                int number = this.Elements.Count(e => !e.IsNamespaceTracking);  
                return string.Format("{0}/{1}", number, this.Elements.Count);  
            }  
  
            #region Value changed handler for the tracked property  
  
            // When a tracked property changes, it needs to notify all of the properties  
            // that track it.  
  
            /// <summary>Called by the DefaultNamespace property value handler when the  
            /// DefaultNamespace property changes.</summary>  
            /// <param name="oldValue">The previous value of the property.</param>  
            /// <param name="newValue">The new value of the property.</param>  
            protected virtual void OnDefaultNamespaceChanged(  
                string oldValue, string newValue)  
            {  
                // Use the helper class to notify all of the elements in the model  
                // that the default namespace has changed.  
                TrackingHelper.UpdateTrackingCollectionProperty(  
                    this.Store,  
                    this.Elements,  
                    ExampleElement.NamespaceDomainPropertyId,  
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);  
            }  
  
            // Update the change handler for the DefaultNamespace property.  
            internal sealed partial class DefaultNamespacePropertyHandler  
            {  
                /// <summary>Called when the DefaultNamespace property changes.</summary>  
                /// <param name="element">The model element that has the property that  
                /// changed.</param>  
                /// <param name="oldValue">The previous value of the property.</param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleModel element, string oldValue, string newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
  
                    if (!element.Store.InUndoRedoOrRollback)  
                    {  
                        element.OnDefaultNamespaceChanged(oldValue, newValue);  
                    }  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-tracking-property"></a>Adicionando código personalizado para a propriedade de controle  
 Adicionar um `CalculateNamespace` método para o `ExampleElement` classe de domínio.  
  
 Definir este método fornece a lógica para a propriedade CustomElements calculado de `ExampleModel`. Esse método conta o número de `ExampleElement` classes de domínio que têm um Namespace de controle de propriedade que está em atualizado pelo estado do usuário e retorna uma cadeia de caracteres que representa essa contagem como uma proporção dos elementos total no modelo.  
  
 Além disso, adicionar armazenamento e métodos para obter e definir a propriedade de armazenamento personalizado de Namespace do `ExampleElement` classe de domínio.  
  
> [!NOTE]
>  O código que as ferramentas de DSL gerar para `ExampleModel` chamadas get e definir métodos; no entanto, as ferramentas de DSL não geram código que implementa os métodos.  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Para adicionar o método para o descritor de tipo personalizado  
  
1.  Adicione o seguinte código ao arquivo NamespaceTrackingProperty.cs.  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the domain class that has the tracking property, add the caluclation  
        // for when the property is tracking.  
        public partial class ExampleElement  
        {  
            /// <summary>Calculates the actual value of the property when it is  
            /// tracking.</summary>  
            /// <returns>The value of the tracking property when it is  
            /// tracking.</returns>  
            /// <remarks>Making this method virtual allows child classes to modify  
            /// the calculation. This method does not need to perform validation, as  
            /// its caller handles validation prior to calling this method.  
            /// <para>In this case, the tracking value depends on the default namespace  
            /// property of the parent model.</para></remarks>  
            protected virtual string CalculateNamespace()  
            {  
                return this.ExampleModel.DefaultNamespace;  
            }  
  
            #region Tracking property implementation  
  
            // Implement the Namespace domain property of the ExampleElement domain class,  
            // and update the IsNamespaceTracking domain property value handler.  
  
            /// <summary>Storage for the Namespace property.</summary>  
            private string namespaceStorage;  
  
            /// <summary>Gets the value of the Namespace property.</summary>  
            /// <returns>The value of the Namespace property.</returns>  
            private string GetNamespaceValue()  
            {  
                // Only retrieve the tracked value if the store is not in the  
                // middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!loading && this.IsNamespaceTracking)  
                {  
                    try  
                    {  
                        return this.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                        return default(string);  
                    }  
                    catch (Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                        else  
                        {  
                            return default(string);  
                        }  
                    }  
                }  
  
                return namespaceStorage;  
            }  
  
            /// <summary>Sets the value of the Namespace property.</summary>  
            /// <param name="value">The new value for the property.</param>  
            private void SetNamespaceValue(string value)  
            {  
                namespaceStorage = value;  
  
                // Only update the state of the tracking property if the store is  
                // not in the middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!this.Store.InUndoRedoOrRollback && !loading)  
                {  
                    this.IsNamespaceTracking = false;  
                }  
            }  
  
            // Update the default behavior of the ExampleElement.IsNamespaceTracking  
            // domain property value handler.  
            internal sealed partial class IsNamespaceTrackingPropertyHandler  
            {  
                /// <summary>Called after the IsNamespaceTracking property changes.  
                /// </summary>  
                /// <param name="element">The model element that has the property  
                /// that changed.</param>  
                /// <param name="oldValue">The previous value of the property.  
                /// </param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleElement element, Boolean oldValue, Boolean newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
                    if (!element.Store.InUndoRedoOrRollback && newValue)  
                    {  
                        DomainPropertyInfo propInfo =  
                            element.Store.DomainDataDirectory.GetDomainProperty(  
                                ExampleElement.NamespaceDomainPropertyId);  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
  
                /// <summary>Performs the reset operation for the IsNamespaceTracking  
                /// property for a model element.</summary>  
                /// <param name="element">The model element that has the property  
                /// to reset.</param>  
                internal void ResetValue(ExampleElement element)  
                {  
                    object calculatedValue = null;  
  
                    try  
                    {  
                        calculatedValue = element.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                    }  
                    catch (System.Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                    }  
  
                    if ((calculatedValue != null  
                        && object.Equals(element.Namespace, calculatedValue)))  
                    {  
                        element.isNamespaceTrackingPropertyStorage = true;  
                    }  
                }  
  
                /// <summary>Method to set IsNamespaceTracking to false so that this  
                /// instance of this tracking property is not storage-based.  
                /// </summary>  
                /// <param name="element">The element on which to reset the property  
                /// value.</param>  
                internal void PreResetValue(ExampleElement element)  
                {  
                    // Force the IsNamespaceTracking property to false so that the value  
                    // of the Namespace property is retrieved from storage.  
                    element.isNamespaceTrackingPropertyStorage = false;  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-to-support-serialization"></a>Adicionando código personalizado para oferecer suporte à serialização  
 Adicione código para dar suporte o comportamento de pós-carga personalizado para serialização de XML.  
  
> [!NOTE]
>  O código que as ferramentas de DSL gerar chamadas a `OnPostLoadModel` e `OnPostLoadModelAndDiagram` métodos; no entanto, as ferramentas de DSL não geram código que implementa esses métodos.  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Para adicionar código para oferecer suporte o comportamento de pós-carregamento de personalizado  
  
1.  Adicione o seguinte código ao arquivo Serialization.cs.  
  
    ```csharp  
    using System;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        #region Helper classes for maintaining state while the store is serializing.  
  
        public abstract partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Reset the tracking state properties to their natural values  
            /// based on comparing storage with calculation.</summary>  
            /// <param name="store">The store that contains this model.</param>  
            internal static void ResetTrackingProperties(Store store)  
            {  
                // Two passes required - one to set all elements to storage-based  
                // then another to set some back to being tracking.  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.PreResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.ResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
            }  
        }  
  
        // Add the pre-reset and reset methods for the model element.  
        public partial class ExampleElement  
        {  
            /// <summary>Calls the pre-reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void PreResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);  
            }  
  
            /// <summary>Calls the reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void ResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);  
            }  
        }  
  
        #endregion  
  
        #region Custom serialization code  
  
        // To the serialization helper for the TrackingPropertyDSL class, add post  
        // load handlers to bind the tracking property to the serialization process.  
        // These handlers manage the tracking states and property values when the  
        // model is serialized and deserialized.  
        public partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Customize model loading.</summary>  
            /// <param name="serializationResult">The serialization result from the  
            /// load operation.</param>  
            /// <param name="partition">The partition in which the new  
            /// instance was created.</param>  
            /// <param name="fileName">The name of the file from which the  
            /// instance was deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.  
            /// </param>  
            private void OnPostLoadModel(  
                SerializationResult serializationResult,  
                Partition partition,  
                string fileName,  
                ExampleModel modelRoot)  
            {  
            }  
  
            /// <summary>Customize model and diagram loading.</summary>  
            /// <param name="serializationResult">Stores serialization result from  
            /// the load operation.</param>  
            /// <param name="modelPartition">Partition in which the new  
            /// instance will be created.</param>  
            /// <param name="modelFileName">Name of the file from which the  
            /// instance will be deserialized.</param>  
            /// <param name="diagramPartition">Partition in which the new  
            /// diagram instance will be created.</param>  
            /// <param name="diagramFileName">Name of the file from which the  
            /// diagram instance will be deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.</param>  
            /// <param name="diagram">The diagram matching the modelRoot.</param>  
            private void OnPostLoadModelAndDiagram(  
                SerializationResult serializationResult,  
                Partition modelPartition,  
                string modelFileName,  
                Partition diagramPartition,  
                string diagramFileName,  
                ExampleModel modelRoot,  
                TrackingPropertyDSLDiagram diagram)  
            {  
                Debug.Assert(modelPartition != null);  
                Debug.Assert(modelPartition.Store != null);  
  
                // Tracking properties need to be set up according to whether the  
                // serialization matches the calculated values.  
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(  
                    modelPartition.Store);  
            }  
        }  
  
        #endregion  
    }  
    ```  
  
## <a name="testing-the-language"></a>Teste o idioma  
 A próxima etapa é criar e executar o designer DSL em uma nova instância de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] para que você possa verificar se a propriedade do controle está funcionando corretamente.  
  
#### <a name="to-exercise-the-language"></a>Para utilizar o idioma  
  
1.  Sobre o **criar** menu, clique em **recompilar solução**.  
  
2.  No menu **Depuração**, clique em **Iniciar Depuração**.  
  
     A compilação experimental de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] abre o **depuração** solução, que contém um arquivo de teste vazio.  
  
3.  Em **Solution Explorer**, duas vezes no arquivo Test.trackingPropertyDsl para abri-lo no designer e, em seguida, clique na superfície de design.  
  
     Observe que no **propriedades** janela para o diagrama, o **Namespace padrão** é de propriedade **DefaultNamespace**e o **elementos personalizados** é de propriedade **0/0**.  
  
4.  Arraste um **ExampleElement** elemento a partir de **caixa de ferramentas** à superfície do diagrama.  
  
5.  No **propriedades** janela para o elemento, selecione o **Namespace do elemento** propriedade e altere o valor de **DefaultNamespace** para ** OtherNamespace**.  
  
     Observe que o valor de **Namespace do elemento** agora é mostrado em negrito.  
  
6.  No **propriedades** janela, clique com botão direito **Namespace do elemento**e, em seguida, clique em **redefinir**.  
  
     O valor da propriedade é alterado para **DefaultNamespace**, e o valor é mostrado em uma fonte regular.  
  
     Clique com botão direito **Namespace do elemento** novamente. O **redefinir** comando agora está desabilitado porque a propriedade está no estado de controle.  
  
7.  Arraste outro **ExampleElement** do **caixa de ferramentas** para a superfície do diagrama e altere seu **Namespace do elemento** para **OtherNamespace**.  
  
8.  Clique na superfície de design.  
  
     No **propriedades** janela para o diagrama, o valor de **elementos personalizados** agora é **1/2**.  
  
9. Alterar **Namespace padrão** para o diagrama de **DefaultNamespace** para **NewNamespace**.  
  
     O **Namespace** as faixas de elemento primeiro o **Namespace padrão** propriedade, enquanto o **Namespace** do segundo elemento retém seu valor de usuário atualizadas de ** OtherNamespace**.  
  
10. Salve a solução e, em seguida, feche a compilação experimental.  
  
## <a name="next-steps"></a>Próximas etapas  
 Se você planeja usar o controle de mais de uma propriedade ou implementar propriedades de controle em mais de uma DSL, você pode criar um modelo de texto para gerar o código comum para dar suporte a cada propriedade de controle. Para obter mais informações sobre modelos de texto, consulte [geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [Como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Como criar uma solução de linguagem específica de domínio](../modeling/how-to-create-a-domain-specific-language-solution.md)   

