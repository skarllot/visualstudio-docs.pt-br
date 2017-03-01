---
title: Compilador do VSIX cor | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 6
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
ms.openlocfilehash: d0fa0e56019de08f3a34a74f018732a6a85660f9
ms.lasthandoff: 02/22/2017

---
# <a name="vsix-color-compiler"></a>Compilador de cor do VSIX
A ferramenta de compilador de cor de extensão do Visual Studio é um aplicativo de console que usa um arquivo. XML que representa as cores de temas existentes do Visual Studio e o converte para um pkgdef de arquivo para que essas cores podem ser usados no Visual Studio. Como é fácil comparar as diferenças entre arquivos. XML, essa ferramenta é útil para o gerenciamento de cores personalizadas no controle de origem. Ele também pode ser conectado em ambientes de compilação para que a saída da compilação é um arquivo pkgdef válido.  
  
 **Esquema XML de tema**  
  
 Um arquivo de tema concluída. XML tem esta aparência:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Tema**  
  
 O \<tema > elemento define um tema inteiro. Um tema deve conter pelo menos um \<categoria > elemento. Elementos de tema são definidos como este:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definição**|  
|Nome|[Obrigatório] O nome do tema|  
|GUID|[Obrigatório] GUID do tema (devem corresponder a formatação de GUID)|  
  
 Ao criar cores personalizadas para o Visual Studio, essas cores precisam ser definidos para os seguintes temas. Se nenhuma cor existir um tema específico, o Visual Studio tenta carregar a ausência de cores do tema no claro.  
  
|||  
|-|-|  
|**Nome do tema**|**GUID de tema**|  
|Claro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Escuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Azul|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Alto Contraste|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Categoria**  
  
 O \<categoria > elemento define uma coleção de cores em um tema. Nomes de categoria fornecem agrupamento lógico e devem ser definidos como estritamente possível. Uma categoria deve conter pelo menos um \<cor > elemento. Elementos de categoria são definidos como este:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definição**|  
|Nome|[Obrigatório] O nome da categoria|  
|GUID|[Obrigatório] GUID da categoria (devem corresponder a formatação de GUID)|  
  
 **Cor**  
  
 O \<cor > elemento define uma cor para um componente ou o estado da interface do usuário. O esquema de nomenclatura preferencial para uma cor é [tipo de interface do usuário] [estado]. Não use a palavra "cor", pois é redundante. Uma cor claramente deve indicar o tipo de elemento e a situações ou "estado", para que a cor será aplicada. Uma cor não pode estar vazia e deve conter um ou ambos um \<fundo > e \<em primeiro plano > elemento. Elementos de cor são definidos como este:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definição**|  
|Nome|[Obrigatório] O nome da cor|  
  
 **Plano de fundo e/ou primeiro plano**  
  
 O \<fundo > e \<em primeiro plano > elementos definem o valor de uma cor e o tipo para o plano de fundo ou primeiro plano de um elemento de interface do usuário. Esses elementos não tem nenhum filho.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Atributo**|**Definição**|  
|Tipo|[Obrigatório] O tipo da cor. Ele pode ser um dos seguintes:<br /><br /> *CT_INVALID:* a cor é inválido ou não foi definida.<br /><br /> *CT_RAW:* um valor ARGB bruto.<br /><br /> *CT_COLORINDEX:* NÃO USE.<br /><br /> *CT_SYSCOLOR:* uma cor de sistema do Windows da SysColor.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX uma cor Visual Studio.<br /><br /> *CT_AUTOMATIC:* a cor automática.<br /><br /> *CT_TRACK_FOREGROUND:* NÃO USE.<br /><br /> *CT_TRACK_BACKGROUND:* NÃO USE.|  
|Origem|[Obrigatório] O valor da cor em hexadecimal|  
  
 O esquema no atributo de tipo oferece suporte a todos os valores com suporte pela enumeração __VSCOLORTYPE. No entanto, recomendamos que você use apenas CT_RAW e CT_SYSCOLOR.  
  
 **Todos juntos**  
  
 Este é um exemplo simple de um arquivo de tema válido. XML:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Como usar a ferramenta  
 **Sintaxe**  
  
 VsixColorCompiler \<arquivo XML > \<arquivo PkgDef > \<Args opcional >  
  
 **Argumentos**  
  
||||  
|-|-|-|  
|**Nome do comutador**|**Observações**|**Obrigatório ou opcional**|  
|Sem nome (arquivo. xml)|Isso é o primeiro parâmetro sem nome e é o caminho para o arquivo XML para converter.|Necessária|  
|Sem nome (arquivo pkgdef)|Esse é o segundo parâmetro sem nome e o caminho de saída para o arquivo pkgdef gerado.<br /><br /> Padrão: \<nome do arquivo XML > pkgdef|Opcional|  
|/noLogo|Defina esse sinalizador para de informações de produto e os direitos autorais de impressão.|Opcional|  
|/?|Imprima informações de Ajuda.|Opcional|  
|/help|Imprima informações de Ajuda.|Opcional|  
  
 **Exemplos**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   /NoLogo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Observações  
  
-   Essa ferramenta requer que a versão mais recente do tempo de execução do VC + + esteja instalado.  
  
-   Há suporte para apenas os arquivos individuais. Não há suporte para conversão em massa por meio de caminhos de pastas.  
  
## <a name="sample-output"></a>Saída de exemplo  
 O arquivo pkgdef gerado pela ferramenta será semelhante a de abaixo chaves:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```
