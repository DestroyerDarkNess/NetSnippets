### A string delimiter, it is similar to the "Split" method, but in my opinion I have improved it a lot!

- Accept 1 or 2 delimiters,
- IgnoreCase option
- Delimit from left to right or from right to left.

```vb
        
#Region " Delimit_String Function "
 
    ' // By Elektro H@ker
    '
    ' USAGE:
    '
    ' MsgBox(Delimit_String("Welcome to my new house", "to")) ' my new house
    ' MsgBox(Delimit_String("Welcome to my new house", "to", "house")) ' my new
    ' MsgBox(Delimit_String("Welcome to my new house", "TO", "HoUSe", True)) ' my new
    ' MsgBox(Delimit_String("Welcome to my new house", "house", "to", , "Left")) ' my new
    ' MsgBox(Delimit_String("Welcome to my new house", "TO", "HoUSe", False)) ' False
    ' MsgBox(Delimit_String("Welcome to my new house", "to", "to", , "Left")) ' Index was outside bounds of the array
 
    Private Function Delimit_String(ByVal STR As String, ByVal Delimiter_A As String, Optional ByVal Delimiter_B As String = "", Optional ByVal Ignore_Case As Boolean = False, Optional ByVal Left_Or_Right As String = "Right")
        Dim Compare_Method As Integer = 0 ' Don't ignore case
        If Ignore_Case = True Then Compare_Method = 1 ' Ignore Case
 
        If Not Left_Or_Right.ToUpper = "LEFT" And Not Left_Or_Right.ToUpper = "RIGHT" _
            Then Return False ' Returns false if the Left_Or_Right argument is in incorrect format
 
        If Compare_Method = 0 Then
            If Not STR.Contains(Delimiter_A) Or Not STR.Contains(Delimiter_B) _
                Then Return False ' Returns false if one of the delimiters in NormalCase can 't be found
        Else
            If Not STR.ToUpper.Contains(Delimiter_A.ToUpper) Or Not STR.ToUpper.Contains(Delimiter_B.ToUpper) _
            Then Return False ' Returns false if one of the delimiters in IgnoreCase can 't be found
        End If
 
        Try
            If Left_Or_Right.ToUpper = "LEFT" Then STR = Split(STR, Delimiter_A, , Compare_Method)(0) _
                Else If Left_Or_Right.ToUpper = "RIGHT" Then STR = Split(STR, Delimiter_A, , Compare_Method)(1)
 
            If Delimiter_B IsNot Nothing Then
                If Left_Or_Right.ToUpper = "LEFT" Then STR = Split(STR, Delimiter_B, , Compare_Method)(1) _
                 Else If Left_Or_Right.ToUpper = "RIGHT" Then STR = Split(STR, Delimiter_B, , Compare_Method)(0)
            End If
 
            Return STR ' Returns the splitted string
        Catch ex As Exception
            Return ex.Message ' Returns exception if index is out of range
        End Try
    End Function
 
#End Region

``` 