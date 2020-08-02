### String Is Email


```vb
 
   ' // By Elektro H@cker
    '
    ' USAGE:
    '
    ' MsgBox(String_Is_Email("User@Email.com"))
 
#Region " String Is Email Function "
 
    Private Function String_Is_Email(ByVal Email_String As String)
        Dim Emaill_RegEx As New System.Text.RegularExpressions.Regex("^[A-Za-z0-9][A-Za-z0-9]+\@[A-Za-z0-9]+\.[A-Za-z0-9][A-Za-z0-9]+$")
        If Emaill_RegEx.IsMatch(Email_String) Then Return True Else Return False
    End Function
 
#End Region

``` 