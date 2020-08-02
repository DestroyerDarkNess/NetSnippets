### Example of an overload


```vb
 
    ' Examples:
    '
    ' Test(0)
    ' Test"0")
 
    Sub Test(ByVal Argument As Integer)
        MsgBox("Integer: " & Argument)
    End Sub
 
    Sub Test(ByVal Argument As String)
        MsgBox("String: " & Argument)
    End Sub

``` 