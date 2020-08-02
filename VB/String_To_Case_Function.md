### convert a string to lower, upper, world case or title case, with option to invert the string


```vb
 
#Region " String To Case Function "
 
    ' [ String To Case Function ]
    '
    ' // By Elektro H@cker
    '
    ' Examples :
    '
    ' MsgBox(String_To_Case("ThiS is A TeST", StringCase.Lower))
    ' MsgBox(String_To_Case("ThiS is A TeST", StringCase.Upper))
    ' MsgBox(String_To_Case("ThiS is A TeST", StringCase.Word))
    ' MsgBox(String_To_Case("ThiS is A TeST", StringCase.Title))
    ' MsgBox(String_To_Case("ThiS is A TeST", StringCase.Title, True))
 
    Enum StringCase
        Lower
        Upper
        Title
        Word
    End Enum
 
    Public Function String_To_Case(ByVal Input_String As String, ByVal StringCase As StringCase, Optional ByVal Reverse As Boolean = False) As String
        If Not Input_String = Nothing And Not Input_String = "" Then
            Dim Output_String As String = Nothing
            Select Case StringCase
                Case StringCase.Lower : Output_String = System.Globalization.CultureInfo.CurrentCulture.TextInfo.ToLower(Input_String)
                Case StringCase.Upper : Output_String = System.Globalization.CultureInfo.CurrentCulture.TextInfo.ToUpper(Input_String)
                Case StringCase.Title : Output_String = Char.ToUpper(Input_String(0)) + StrConv(Input_String.Substring(1), VbStrConv.Lowercase)
                Case StringCase.Word : Output_String = System.Globalization.CultureInfo.CurrentCulture.TextInfo.ToTitleCase(Input_String)
            End Select
            If Reverse Then Return Microsoft.VisualBasic.StrReverse(Output_String) Else Return Output_String
        Else : Return False ' Any string to convert
        End If
    End Function
 
#End Region

``` 