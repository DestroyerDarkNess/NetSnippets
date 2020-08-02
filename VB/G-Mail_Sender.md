### G-Mail Sender (Send emails)


```vb
   ' USAGE:
    '
    ' GMail_Sender("Your_Email@Gmail.com", "Your_Password", "Email Subject", "Message Body", "Destiny@Email.com")
 
#Region " GMail Sender function "
 
    Private Function GMail_Sender(ByVal Gmail_Username As String, ByVal Gmail_Password As String, ByVal Email_Subject As String, ByVal Email_Body As String, ByVal Email_Destiny As String)
        Try
            Dim MailSetup As New System.Net.Mail.MailMessage
            MailSetup.Subject = Email_Subject
            MailSetup.To.Add(Email_Destiny)
            MailSetup.From = New System.Net.Mail.MailAddress(Gmail_Username)
            MailSetup.Body = Email_Body
            Dim SMTP As New System.Net.Mail.SmtpClient("smtp.gmail.com")
            SMTP.Port = 587
            SMTP.EnableSsl = True
            SMTP.Credentials = New Net.NetworkCredential(Gmail_Username, Gmail_Password)
            SMTP.Send(MailSetup)
            Return True ' Email is sended OK
        Catch ex As Exception
            Return ex.Message ' Email can't be sended
        End Try
    End Function
 
#End Region

``` 