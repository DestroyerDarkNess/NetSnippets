### Get the ID of the motherboard:


```vb
 
#Region " Get Motherboard ID Function "
 
    ' [ Get Motherboard ID Function ]
    '
    ' Examples :
    '
    ' Dim Motherboard_ID As String = Get_Motherboard_ID()
    ' MsgBox(Get_Motherboard_ID())
 
    Private Function Get_Motherboard_ID() As String
        For Each Motherboard As Object In GetObject("WinMgmts:").InstancesOf("Win32_BaseBoard") : Return Motherboard.SerialNumber : Next Motherboard
        Return Nothing
    End Function
 
#End Region

``` 