### Hotmail sender (Send emails from hotmail)

- It is necessary to download the EASENDMAIL library (It is free although you can buy a license): http://www.emailarchitect.net/webapp/download/easendmail.exe

- I know that this can be done with the class system.net.mail, but with this we do not depend on ports, and the SSL of the servers that we use in the library is automatically detected ...

```vb
 
#Region " Hotmail Sender Function "
 
    ' [ Hotmail Sender Function ]
    '
    ' // By Elektro H@cker
    '
    ' * First add a reference to "EASendMail" into the project.
    '
    ' Examples :
    '
    '  MsgBox(Hotmail_Sender("ElektroHacker@hotmail.com", "MyPass", "Anonym@gmail.com", "Test subject", "Test body", {"C:\File1.txt", "C:\File2.txt"}))
 
    Private Function Hotmail_Sender(ByVal Account_User As String, ByVal Account_Password As String, ByVal Mail_To As String, ByVal Mail_Subject As String, ByVal Mail_Body As String, Optional ByVal Mail_Attachments() As String = Nothing) As Boolean
 
        Dim Hot_Mail As New EASendMail.SmtpMail("TryIt")
        Dim Hot_Server As New EASendMail.SmtpServer("smtp.live.com")
        Dim Hot_Smtp As New EASendMail.SmtpClient()
 
        Hot_Server.User = Account_User
        Hot_Server.Password = Account_Password
        Hot_Server.ConnectType = EASendMail.SmtpConnectType.ConnectSSLAuto
 
        Hot_Mail.From = Account_User
        Hot_Mail.To = Mail_To
        Hot_Mail.Subject = Mail_Subject
        Hot_Mail.TextBody = Mail_Body
        If Mail_Attachments IsNot Nothing Then For Each Attachment In Mail_Attachments : Hot_Mail.AddAttachment(Attachment) : Next
 
        Try : Hot_Smtp.SendMail(Hot_Server, Hot_Mail) : Return True
        Catch ex As Exception : Return False : End Try
 
    End Function
 
#End Region

``` 