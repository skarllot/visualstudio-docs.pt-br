---
title: "Criar um aplicativo simples de dados usando o ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 42
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar um aplicativo simples de dados usando o ADO.NET
Quando você cria um aplicativo que manipule dados em um banco de dados, executar tarefas básicas, tais definindo cadeias de conexão, inserindo dados e executar procedimentos armazenados. Seguindo esse tópico, você pode descobrir como interagir com o banco de dados de dentro de um aplicativo simples de "formulários sobre dados" do Windows Forms usando o Visual c\# ou Visual Basic e ADO.NET.  Todas as tecnologias de dados .NET, inclusive conjuntos de dados, o LINQ to SQL e Entity Framework, por fim, executar etapas muito semelhantes às mostradas neste artigo.  
  
 Este artigo demonstra uma maneira simples de obter dados de um banco de dados de uma maneira muito rápida. Se seu aplicativo precisa modificar dados de formas não triviais e atualizar o banco de dados, em seguida, considere usando o Entity Framework e usando associação de dados para sincronizar automaticamente os controles de interface do usuário para as alterações nos dados subjacentes.  
  
> [!IMPORTANT]
>  Para simplificar o código, ele não inclui tratamento de exceção pronto para produção.  
  
 **Neste tópico**  
  
-   [Configurar o banco de dados de exemplo](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [Criar os formulários e adicionar controles](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [Armazenar a cadeia de conexão](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [Recuperar a cadeia de conexão](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [Escreva o código para os formulários](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [Testar seu aplicativo](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## Pré-requisitos  
 Para criar o aplicativo, você precisará de:  
  
-   Visual Studio Community Edition  
  
-   SQL Server Express LocalDB  
  
-   O banco de dados de exemplo pequeno que você criar seguindo as etapas em [Criar um banco de dados SQL usando um script](../data-tools/create-a-sql-database-by-using-a-script.md).  
  
-   A cadeia de conexão para o banco de dados depois de configurá\-lo. Você pode encontrar esse valor abrindo **Pesquisador de objetos do SQL Server**, abrindo o menu de atalho para o banco de dados, escolhendo **propriedades**, e, em seguida, rolar até o **seqüência de conexão** propriedade.  
  
 Este tópico pressupõe que você esteja familiarizado com a funcionalidade básica do IDE do Visual Studio e pode criar um aplicativo Windows Forms, adicionar formulários para o projeto, colocar botões e outros controles em formulários, definir as propriedades desses controles e eventos simples do código. Se você não estiver familiarizado com essas tarefas, sugerimos que você conclua a [Introdução ao Visual C\# e ao Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) tutoriais antes de iniciar este tópico.  
  
##  <a name="BKMK_setupthesampledatabase"></a> Configurar o banco de dados de exemplo  
 O banco de dados de exemplo para este passo a passo consiste das tabelas clientes e pedidos. As tabelas não contêm dados inicialmente, mas você adicionará dados quando você executar o aplicativo que você criará. O banco de dados também tem cinco procedimentos armazenados simples.[Criar um banco de dados SQL usando um script](../data-tools/create-a-sql-database-by-using-a-script.md) contém um script Transact\-SQL que cria as tabelas, as chaves primária e estrangeiras, as restrições e os procedimentos armazenados.  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> Criar os formulários e adicionar controles  
  
1.  Criar um projeto para um aplicativo Windows Forms e nomeie\-a como `SimpleDataApp`.  
  
     Visual Studio cria o projeto e vários arquivos, inclusive um formulário vazio do Windows chamado Form1.  
  
2.  Adicione dois formulários do Windows ao seu projeto para que ele tenha três formulários e dar\-lhes nomes a seguir.  
  
    -   Navegação  
  
    -   NewCustomer  
  
    -   FillOrCancel  
  
3.  Para cada formulário, adicione as caixas de texto, botões e outros controles que aparecem nas ilustrações a seguir. Para cada controle, defina as propriedades que descrevem as tabelas.  
  
    > [!NOTE]
    >  A caixa de grupo e os controles de rótulo adicionar clareza, mas não são usados no código.  
  
 **Formulário de navegação**  
  
 ![Navigation dialog box](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Controles do formulário de navegação|Propriedades|  
|------------------------------------------|------------------|  
|Botão|Nome \= btnGoToAdd|  
|Botão|Nome \= btnGoToFillOrCancel|  
|Botão|Nome \= btnExit|  
  
 **Formulário de NewCustomer**  
  
 ![Add  a new customer and place an order](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|Controles do formulário NewCustomer|Propriedades|  
|-----------------------------------------|------------------|  
|Caixa de texto|Nome \= txtCustomerName|  
|Caixa de texto|Nome \= txtCustomerID<br /><br /> ReadOnly \= True|  
|Botão|Nome \= btnCreateAccount|  
|NumericUpdown|DecimalPlaces \= 0<br /><br /> Máximo \= 5000<br /><br /> Nome \= numOrderAmount|  
|DateTimePicker|Formato \= curto<br /><br /> Nome \= dtpOrderDate|  
|Botão|Nome \= btnPlaceOrder|  
|Botão|Nome \= btnAddAnotherAccount|  
|Botão|Nome \= btnAddFinish|  
  
 **Formulário FillOrCancel**  
  
 ![fill or cancel orders](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|Controles do formulário FillOrCancel|Propriedades|  
|------------------------------------------|------------------|  
|Caixa de texto|Nome \= txtOrderID|  
|Botão|Nome \= btnFindByOrderID|  
|DateTimePicker|Formato \= curto<br /><br /> Nome \= dtpFillDate|  
|DataGridView|Nome \= dgvCustomerOrders<br /><br /> ReadOnly \= True<br /><br /> RowHeadersVisible \= False|  
|Botão|Nome \= btnCancelOrder|  
|Botão|Nome \= btnFillOrder|  
|Botão|Nome \= btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> Armazenar a cadeia de conexão  
 Quando o aplicativo tenta abrir uma conexão com o banco de dados, seu aplicativo deve ter acesso à cadeia de conexão. Para evitar inserir a cadeia de caracteres manualmente em cada formulário, armazenar a cadeia de caracteres no arquivo de configuração do aplicativo em seu projeto e crie um método que retorna a cadeia de caracteres quando chamado a partir de qualquer forma em seu aplicativo.  
  
 A cadeia de conexão pode ser encontrada no SQL Server Object Explorer, clicando duas vezes no banco de dados, escolha Propriedades e, em seguida, localizar a propriedade ConnectionString. Use Ctrl\-A para selecionar a cadeia de caracteres.  
  
1.  No Solution Explorer, escolha **propriedades** nó sob o projeto e, em seguida, escolha Settings.  
  
2.  No **nome** coluna, digite `connString`.  
  
3.  No **tipo** escolha **\(cadeia de caracteres de conexão\)**.  
  
4.  No **escopo** escolha **aplicativo**.  
  
5.  No **valor** coluna, insira a cadeia de conexão \(sem qualquer fora aspas\) e, em seguida, salvar as alterações.  
  
> [!NOTE]
>  Em um aplicativo real, você deve armazenar a cadeia de conexão segura, conforme descrito em [Cadeias de conexão e arquivos de configuração](../Topic/Connection%20Strings%20and%20Configuration%20Files.md)  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> Recuperar a cadeia de conexão  
  
1.  Na barra de menus, escolha **projeto**, **Adicionar referência**, e, em seguida, adicione uma referência para o System.Configuration.dll.  
  
2.  Na barra de menus, escolha **projeto**, **Add Class** para adicionar um arquivo de classe ao seu projeto e, em seguida, nomeie o arquivo `Utility`.  
  
     Visual Studio cria o arquivo e exibe\-o em **Solution Explorer**.  
  
3.  No arquivo de utilitário, substitua o código de espaço reservado com o código a seguir. Observe os comentários numerados \(prefixados com Util\-\) que identificam seções do código. A tabela a seguir o código chama pontos\-chave.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    //Util-1 More namespaces.  
    using System.Configuration;   
  
    namespace SimpleDataApp  
    {  
        internal class Utility  
        {  
  
            //Get the connection string from App config file.  
            internal static string GetConnectionString()  
            {  
                //Util-2 Assume failure.  
                string returnValue = null;  
  
                //Util-3 Look for the name in the connectionStrings section.  
                ConnectionStringSettings settings =  
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];  
  
                //If found, return the connection string.  
                if (settings != null)  
                    returnValue = settings.ConnectionString;  
  
                return returnValue;  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Linq  
    Imports System.Text  
    Imports System.Threading.Tasks  
    ' Util-1 More namespaces.  
    Imports System.Configuration  
  
    Namespace SimpleDataApp  
        Friend Class Utility  
  
            ' Get connection string from App config file.  
            Friend Shared Function GetConnectionString() As String  
  
                ' Util-2 Assume failure.  
                Dim returnValue As String = Nothing  
  
                ' Util-3 Look for the name in the connectionStrings section.  
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")  
  
                ' If found, return the connection string.  
                If settings IsNot Nothing Then  
                    returnValue = settings.ConnectionString  
                End If  
  
                Return returnValue  
            End Function  
        End Class  
    End Namespace  
    ```  
  
    |Comentário|Descrição|  
    |----------------|---------------|  
    |Util\-1|Adicione o namespace System. Configuration.|  
    |Util\-2|Definir uma variável, `returnValue`, e inicializá\-lo para `null` \(c\#\) ou `Nothing` \(Visual Basic\).|  
    |Util\-3|Mesmo que você inseriu `connString` como o nome da cadeia de conexão no **propriedades** janela, você deve especificar `"SimpleDataApp.Properties.Settings.connString"` \(c\#\) ou `"SimpleDataApp.My.MySettings.connString"` \(Visual Basic\) no código.|  
  
##  <a name="BKMK_writethecodefortheforms"></a> Escreva o código para os formulários  
 Esta seção contém uma visão geral breve do que faz cada formulário e mostra o código que cria os formulários. Numerada comentários identificam seções do código.  
  
### Formulário de navegação  
 O formulário de navegação abre quando você executar o aplicativo. O **Adicionar uma conta** botão abre o formulário NewCustomer. O **preenchimento ou cancelar pedidos** botão abre o formulário FillOrCancel. O **Exit** botão fecha o aplicativo.  
  
#### Tornar a navegação formam o formulário de inicialização  
 Se você estiver usando c\#, em **Solution Explorer**, abra Program.cs e, em seguida, alterar o `Application.Run` linha a esta: `Application.Run(new Navigation());`  
  
 Se você estiver usando Visual Basic, em **Solution Explorer**, abra o **propriedades** janela, escolha o **aplicativo** guia e, em seguida, escolha SimpleDataApp.Navigation o **formulário de inicialização** lista.  
  
#### Criar manipuladores de eventos  
 Clique duas vezes em três botões no formulário para criar métodos de manipulador de eventos vazio.  
  
#### Criar código para navegação  
 No formulário de navegação, substitua o código existente pelo código a seguir.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
  
namespace SimpleDataApp  
{  
    public partial class Navigation : Form  
    {  
        public Navigation()  
        {  
            InitializeComponent();  
        }  
  
        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        private void btnGoToAdd_Click(object sender, EventArgs e)  
        {  
            Form frm = new NewCustomer();  
            frm.Show();  
        }  
  
        //Open the FillorCancel form as a dialog box.  
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)  
        {  
            Form frm = new FillOrCancel();  
            frm.ShowDialog();  
        }  
  
        //Close the application, not just the Navigation form.  
        private void btnExit_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
  
Namespace SimpleDataApp  
    Partial Public Class Navigation  
        Inherits Form  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click  
            Dim frm As Form = New NewCustomer()  
            frm.Show()  
        End Sub  
  
        ' Open the FillorCancel form as a dialog box.  
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click  
            Dim frm As Form = New FillOrCancel()  
            frm.ShowDialog()  
        End Sub  
  
        ' Close the application, not just the Navigation form.  
        Private Sub btnExit_Click() Handles btnExit.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
  
```  
  
### Formulário de NewCustomer  
 Quando você inserir um nome de cliente e, em seguida, escolha o **Criar conta** botão, o formulário NewCustomer cria uma conta de cliente e o SQL Server retorna um valor de identidade como o novo número da conta. Coloque um pedido para a nova conta, especificando um valor e a data do pedido e escolhendo o **Fazer pedido** botão.  
  
#### Criar manipuladores de eventos  
 Criar um vazio, clique em manipulador de eventos para cada botão no formulário.  
  
#### Criar código para NewCustomer  
 Adicione o seguinte código ao formulário NewCustomer. Percorra cada bloco de código usando os comentários numerados e a tabela após o código.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//NC-1 More namespaces.  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class NewCustomer : Form  
    {  
        //NC-2 Storage for IDENTITY values returned from database.  
        private int parsedCustomerID;  
        private int orderID;  
  
        //NC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public NewCustomer()  
        {  
            InitializeComponent();  
        }  
  
        //NC-4 Create account.  
        private void btnCreateAccount_Click(object sender, EventArgs e)  
        {  
            //NC-5 Set up and run stored procedure only if Customer Name is present.  
            if (isCustomerName())  
            {  
  
                //NC-6 Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;  
  
                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));  
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;  
  
                //NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;  
  
                //NC-10 try-catch-finally  
                try  
                {  
                    //NC-11 Open the connection.  
                    conn.Open();  
  
                    //NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery();  
  
                    //NC-13 Customer ID is an IDENTITY value from the database.   
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;  
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);  
  
                }  
                catch  
                {  
                    //NC-14 A simple catch.  
  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.");  
                }  
                finally  
                {  
                    //NC-15 Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-16 Verify that Customer Name is present.  
        private bool isCustomerName()  
        {  
            if (txtCustomerName.Text == "")  
            {  
                MessageBox.Show("Please enter a name.");  
                return false;  
            }  
            else  
            {  
                return true;  
            }  
        }  
  
        //NC-17 Place order.  
        private void btnPlaceOrder_Click(object sender, EventArgs e)  
        {  
            //NC-18 Set up and run stored procedure only if required input is present.  
            if (isPlaceOrderReady())  
            {  
                // Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-19 Create SqlCommand and identify it as a stored procedure.  
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);  
                cmdNewOrder.CommandType = CommandType.StoredProcedure;  
  
                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;  
  
                //NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));  
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;  
  
                //NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));  
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;  
  
                //NC-23 @Status. For a new order, the status is always O (open)  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is the orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try – catch - finally  
                try  
                {  
                    //Open connection.  
                    conn.Open();  
  
                    //Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery();  
  
                    //NC-25 Display the order number.  
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;  
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("Order could not be placed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-26 Verify that order data is ready.  
        private bool isPlaceOrderReady()  
        {  
            // Verify that CustomerID is present.  
            if (txtCustomerID.Text == "")  
            {  
                MessageBox.Show("Please create customer account before placing order.");  
                return false;  
            }  
  
            // Verify that Amount isn't 0.   
            else if ((numOrderAmount.Value < 1))  
            {  
                MessageBox.Show("Please specify an order amount.");  
                return false;  
            }  
            else  
            {  
                // Order can be submitted.  
                return true;  
            }  
        }  
  
        //NC-27 Reset the form for another new account  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls  
        private void ClearForm()  
        {  
            txtCustomerName.Clear();  
            txtCustomerID.Clear();  
            dtpOrderDate.Value = DateTime.Now;  
            numOrderAmount.Value = 0;  
            this.parsedCustomerID = 0;  
        }  
  
        //NC-29 Close the form.  
        private void btnAddFinish_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
  
    }  
}  
  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' NC-1 More namespaces.  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class NewCustomer  
        Inherits Form  
  
        ' NC-2 Storage for IDENTITY values returned from database.  
        Private parsedCustomerID As Integer  
        Private orderID As Integer  
  
        ' NC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' NC-4 Create account.  
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click  
  
            ' NC-5 Set up and run stored procedure only if Customer Name is present.  
            If isCustomerName() Then  
  
                ' NC-6 Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure  
  
                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))  
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text  
  
                ' NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output  
  
                ' NC-10 try-catch-finally  
                Try  
                    ' NC-11 Open the connection.  
                    conn.Open()  
  
                    ' NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery()  
  
                    ' NC-13 Customer ID is an IDENTITY value from the database.   
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)  
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)  
  
                Catch  
                    ' NC-14 A simple catch.  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")  
                Finally  
                    ' NC-15 Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-16 Verify that Customer Name is present.  
        Private Function isCustomerName() As Boolean  
            If txtCustomerName.Text = "" Then  
                MessageBox.Show("Please enter a name.")  
                Return False  
            Else  
                Return True  
            End If  
        End Function  
  
        ' NC-17 Place order.  
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click  
  
            ' NC-18 Set up and run stored procedure only if necessary input is present.  
            If isPlaceOrderReady() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-19 Create SqlCommand and identify it as a stored procedure.  
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)  
                cmdNewOrder.CommandType = CommandType.StoredProcedure  
  
                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID  
  
                ' NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))  
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value  
  
                ' NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))  
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value  
  
                ' NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))  
                cmdNewOrder.Parameters("@Status").Value = "O"  
  
                ' NC-24 add return value for stored procedure, which is the orderID  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try – catch - finally  
                Try  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery()  
  
                    ' NC-25 Display the order number.  
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)  
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")  
  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("Order could not not be placed.")  
  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-26 Verify that order data is ready.  
        Private Function isPlaceOrderReady() As Boolean  
  
            ' Verify that CustomerID is present.  
            If txtCustomerID.Text = "" Then  
                MessageBox.Show("Please create customer account before placing order.")  
                Return False  
  
                ' Verify that Amount isn't 0   
            ElseIf (numOrderAmount.Value < 1) Then  
  
                MessageBox.Show("Please specify an order amount.")  
                Return False  
            Else  
                ' Order can be submitted.  
                Return True  
            End If  
        End Function  
  
        ' NC-27 Reset the form for another new account.  
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click  
            Me.ClearForm()  
        End Sub  
  
        ' NC-28 Clear values from controls.  
        Private Sub ClearForm()  
            txtCustomerName.Clear()  
            txtCustomerID.Clear()  
            dtpOrderDate.Value = DateTime.Now  
            numOrderAmount.Value = 0  
            Me.parsedCustomerID = 0  
        End Sub  
  
        ' NC-29 Close the form.  
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click  
            Me.Close()  
        End Sub  
  
    End Class  
End Namespace  
```  
  
|Comentário|Descrição|  
|----------------|---------------|  
|NC\-1|Adicione System.Data.SqlClient e System. Configuration à lista de namespaces.|  
|NC\-2|Declarar o `parsedCustomerID` e `orderID` as variáveis que você usará mais tarde.|  
|NC\-3|Chamar o `GetConnectionString` método para obter a cadeia de conexão do arquivo de configuração do aplicativo e armazenar o valor na `connstr` variável de cadeia de caracteres.|  
|NC\-4|Adicione código para o manipulador de eventos para o `btnCreateAccount` botão.|  
|NC\-5|Encapsular a chamada para `isCustomerName` no código de evento Click para que `uspNewCustomer` é executado somente se houver um nome de cliente.|  
|NC\-6|Criar um `SqlConnection` objeto \(`conn`\) e passe a cadeia de conexão em `connstr`.|  
|NC\-7|Criar um `SqlCommand` objeto, `cmdNewCustomer`.<br /><br /> -   Especifique `Sales.uspNewCustomer` como o procedimento armazenado para executar.<br />-   Use o `CommandType` propriedade para especificar que o comando é um procedimento armazenado.|  
|NC\-8|Adicionar o `@CustomerName` parâmetro de entrada do procedimento armazenado.<br /><br /> -   Adicione o parâmetro para o `Parameters` coleção.<br />-   Use a enumeração SqlDbType para especificar o tipo de parâmetro como nvarchar \(40\).<br />-   Especifique `txtCustomerName.Text` como a origem.|  
|NC\-9|Adicione o parâmetro de saída do procedimento armazenado.<br /><br /> -   Adicione o parâmetro para o `Parameters` coleção.<br />-   Use `ParameterDirection.Output` para identificar o parâmetro de saída.|  
|NC\-10|Adicione um bloco Try – Catch – bloco Finally para abrir a conexão, execute o procedimento armazenado, manipular exceções e, em seguida, feche a conexão.|  
|NC\-11|Abrir a conexão \(`conn`\) que você criou no NC\-6.|  
|NC\-12|Use `cmdNewCustomer`do `ExecuteNonQuery` método para executar o `Sales.uspNewCustomer` procedimento armazenado, que executa um `INSERT` instrução, não uma consulta.|  
|NC\-13|O `@CustomerID` valor é retornado como um valor de identidade do banco de dados. Porque ele é um número inteiro, você precisará convertê\-lo em uma cadeia de caracteres para exibi\-lo na caixa de texto ID do cliente.<br /><br /> -   Você declarado `parsedCustomerID` no NC\-2.<br />-   Armazenamento de `@CustomerID` valor `parsedCustomerID` para uso posterior.<br />-   Converter a ID de cliente retornado em uma cadeia de caracteres e inseri\-lo em `txtCustomerID.Text`.|  
|NC\-14|Para este exemplo, adicione uma cláusula catch simples, não da qualidade de produção.|  
|NC\-15|Feche uma conexão sempre depois de terminar de usá\-la, para que ele pode ser liberado para o pool de conexões. Consulte [\(ADO.NET\) de pool de conexão do SQL Server](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|  
|NC\-16|Defina um método para verificar se um nome de cliente está presente.<br /><br /> -   Se a caixa de texto estiver vazia, exibir uma mensagem e retornar `false`, porque é necessário um nome para criar a conta.<br />-   Se a caixa de texto não estiver vazia, retorne `true`.|  
|NC\-17|Adicione código para o manipulador de eventos para o `btnPlaceOrder` botão.|  
|NC\-18|Encapsular a chamada para `isPlaceOrderReady` em torno de `btnPlaceOrder_Click` código de evento para que `uspPlaceNewOrder` não é executado se necessário a entrada não estiver presente.|  
|NC\-19 a 25 NC|Essas seções de código se parecer com o código que você adicionou o `btnCreateAccount_Click` manipulador de eventos.<br /><br /> -   NC\-19. Crie o `SqlCommand` objeto, `cmdNewOrder`, e especifique `Sales.uspPlaceOrder` como o procedimento armazenado.<br />-   NC\-20 a 23 NC são os parâmetros de entrada para o procedimento armazenado.<br />-   NC\-24.`@RC` contém um valor de retorno é a identificação do pedido gerado do banco de dados. Direção deste parâmetro é especificada como `ReturnValue`.<br />-   NC\-25. Armazenar o valor da ID de ordem no `orderID` variável declarada no NC\-2 e exibir o valor em uma caixa de mensagem.|  
|NC 26|Defina um método para verificar se existe uma ID de cliente e que um valor foi especificado em `numOrderAmount`.|  
|NC\-27|Chamar o `ClearForm` método o `btnAddAnotherAccount` manipulador de evento.|  
|NC\-28|Crie o `ClearForm` método para limpar os valores do formulário para adicionar outro cliente.|  
|NC29|Feche o formulário NewCustomer e retornar o foco para o formulário de navegação.|  
  
### Formulário FillOrCancel  
 O formulário FillorCancel executa uma consulta para retornar um pedido quando você inserir uma identificação do pedido e escolha o **Localizar ordem** botão. A linha retornada é exibida em uma grade de dados somente leitura. Você pode marcar a ordem como cancelada \(X\), se você escolher o **Cancelar pedido** botão, ou você pode marcar a ordem como preenchido \(F\) se você escolher o **ordem preencher** botão. Se você escolher o **Localizar ordem** novamente, a linha atualizada é exibida.  
  
#### Criar manipuladores de eventos  
 Criar vazia clique em manipuladores de eventos para os quatro botões no formulário.  
  
#### Criar código para FillOrCancel  
 Adicione o seguinte código ao formulário FillOrCancel. Percorra os blocos de código usando os comentários numerados e a tabela que segue o código.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//FC-1 More namespaces.  
using System.Text.RegularExpressions;  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class FillOrCancel : Form  
    {  
        //FC-2 Storage for OrderID.  
        private int parsedOrderID;  
  
        //FC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public FillOrCancel()  
        {  
            InitializeComponent();  
        }  
  
        //FC-4 Find an order.  
        private void btnFindByOrderID_Click(object sender, EventArgs e)  
        {  
            //FC-5 Prepare the connection and the command  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Define a query string that has a parameter for orderID.  
                string sql = "select * from Sales.Orders where orderID = @orderID";  
  
                //Create a SqlCommand object.  
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);  
  
                //Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;  
  
                //try – catch - finally  
                try  
                {  
                    //FC-6 Run the command and display the results.  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the command by using SqlDataReader.  
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();  
  
                    //Create a data table to hold the retrieved data.  
                    DataTable dataTable = new DataTable();  
  
                    //Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr);  
  
                    //Display the data from the datatable in the datagridview.  
                    this.dgvCustomerOrders.DataSource = dataTable;  
  
                    //Close the SqlDataReader.  
                    rdr.Close();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-7 Cancel an order.  
        private void btnCancelOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                // Create command and identify it as a stored procedure.  
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;  
  
                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                // try-catch-finally  
                try  
                {  
                    // Open the connection.  
                    conn.Open();  
  
                    // Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery();  
                }  
                // A simple catch.  
                catch  
                {  
                    MessageBox.Show("The cancel operation was not completed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-8 Fill an order.  
        private void btnFillOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Create command and identify it as a stored procedure.  
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);  
                cmdFillOrder.CommandType = CommandType.StoredProcedure;  
  
                // Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                //Add the second input parameter.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));  
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;  
  
                //try – catch - finally  
                try  
                {  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the cmdFillOrder command.  
                    cmdFillOrder.ExecuteNonQuery();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The fill operation was not completed.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-9 Verify that OrderID is ready.  
        private bool isOrderID()  
        {  
  
            //Check for input in the Order ID text box.  
            if (txtOrderID.Text == "")  
            {  
                MessageBox.Show("Please specify the Order ID.");  
                return false;  
            }  
  
            // Check for characters other than integers.  
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))  
            {  
               //Show message and clear input.  
                MessageBox.Show("Please specify integers only.");  
                txtOrderID.Clear();  
                return false;  
            }  
            else  
            {  
                //Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text);  
                return true;  
            }  
        }  
  
        //Close the form.  
        private void btnFinishUpdates_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' FC-1 More namespaces.  
Imports System.Text.RegularExpressions  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class FillOrCancel  
        Inherits Form  
        ' FC-2 Storage for OrderID  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' FC-4 Find an order.  
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click  
  
            ' FC-5 Prepare the connection and the command.  
  
            If isOrderID() Then  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Define the query string that has a parameter for orderID.  
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"  
  
                ' Create a SqlCommand object.  
                Dim cmdOrderID As New SqlCommand(sql, conn)  
  
                ' Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' FC-6 Run the command and display the results.  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the command by using SqlDataReader.  
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()  
  
                    ' Create a data table to hold the retrieved data.  
                    Dim dataTable As New DataTable()  
  
                    ' Load the data from the SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the datagridview.  
                    Me.dgvCustomerOrders.DataSource = dataTable  
  
                    ' Close the SqlDataReader.  
                    rdr.Close()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-7 Cancel an order.  
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create the command and identify it as a stored procedure.  
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The cancel operation was not completed.")  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-8 Fill an order.  
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create command and identify it as a stored procedure.  
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)  
                cmdFillOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' Add second input parameter.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))  
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdFillOrder command.   
                    cmdFillOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The fill operation was not completed.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-9 Verify that OrderID is ready.  
        Private Function isOrderID() As Boolean  
  
            ' Check for input in the Order ID text box.  
            If txtOrderID.Text = "" Then  
                MessageBox.Show("Please specify the Order ID.")  
                Return False  
  
                ' Check for characters other than integers.  
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then  
  
                ' Show message and clear input.  
                MessageBox.Show("Please specify integers only.")  
                txtOrderID.Clear()  
                Return False  
  
            Else  
                ' Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text)  
                Return True  
  
            End If  
        End Function  
  
        ' Close the form.  
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
|Comentário|Descrição|  
|----------------|---------------|  
|FC\-1|Adicione System.Text.RegularExpressions, System. Configuration e System.Data.SqlClient à lista de namespaces.|  
|FC\-2|Declarar o `parsedOrderID` variável.|  
|FC\-3|Chamar o `GetConnectionString` método para obter a cadeia de conexão do arquivo de configuração do aplicativo e armazenar o valor na `connstr` variável de cadeia de caracteres.|  
|FC\-4|Adicione código ao manipulador de eventos Click para `btnFindOrderByID`.|  
|FC\-5|Pode parecer familiar? Essas tarefas são necessárias antes de tentar executar uma instrução SQL ou um procedimento armazenado.<br /><br /> -   Crie um objeto SqlConnection.<br />-   Definir a instrução SQL ou especifique o nome do procedimento armazenado. \(Nesse caso, você executará um `SELECT` instrução.\)<br />-   Criar um `SqlCommand` objeto.<br />-   Defina os parâmetros para a instrução SQL ou procedimento armazenado.|  
|FC\-6|Esse código usa `SqlDataReader` e `DataTable` para recuperar e exibir o resultado da consulta.<br /><br /> -   Abra a conexão.<br />-   Criar um SqlDataReader, `rdr`, executando `cmdOrderID`do `ExecuteReader` método.<br />-   Criar um `DataTable` objeto para armazenar os dados recuperados.<br />-   Carregar os dados a partir de `SqlDataReader` no `DataTable` objeto.<br />-   Exibir os dados no datagridview, especificando a `DataTable` como o `DataSource` para datagridview.<br />-   Feche o SqlDataReader.|  
|FC\-7|Adicione código ao manipulador de eventos Click para `btnCancelOrder`. Esse código é executado o `Sales.uspCancelOrder` procedimento armazenado.|  
|FC\-8|Adicione código ao manipulador de eventos Click para `btnFillOrder`. Esse código é executado o `Sales.uspFillOrder` procedimento armazenado.|  
|FC\-9|Crie um método para verificar se o `OrderID` está pronta para enviar como um parâmetro para o `SqlCommand` objeto.<br /><br /> -   Certifique\-se de que uma ID foi inserida no `txtOrderID`.<br />-   Use `Regex.IsMatch` para definir uma verificação simples para caracteres não inteiro.<br />-   Você declarado o `parsedOrderID` variável em FC\-2.<br />-   Se a entrada é válida, converter o texto em um número inteiro e armazenar o valor de `parsedOrderID` variável.<br />-   Encapsular o `isOrderID` método em torno de `btnFindByOrderID`, `btnCancelOrder`, e `btnFillOrder` manipuladores de evento de clique.|  
  
##  <a name="BKMK_testyourapplication"></a> Testar seu aplicativo  
 Escolha a tecla F5 para compilar e testar seu aplicativo depois que você codificar cada manipulador de eventos Click e, em seguida, depois de concluir a codificação.