### String is URL?


```vb
     ' USAGE:
    '
    ' If String_Is_URL("http://google.com") Then MsgBox("Valid url!") Else MsgBox("Invalid url!")
 
#Region " String Is URL Function "
 
    Private Function String_Is_URL(ByVal STR As String)
        Dim URL_Pattern As String = "^(http|https):/{2}[a-zA-Z./&\d_-]+"
        Dim URL_RegEx As New System.Text.RegularExpressions.Regex(URL_Pattern, System.Text.RegularExpressions.RegexOptions.IgnoreCase Or System.Text.RegularExpressions.RegexOptions.ExplicitCapture)
        If URL_RegEx.IsMatch(STR) Then Return True Else Return False
    End Function
 
#End Region
``` 