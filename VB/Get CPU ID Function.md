### Get the processor ID:


```vb
 
#Region " Get CPU ID Function "
 
    ' [ Get CPU ID Function ]
    '
    ' Examples :
    '
    ' Dim Processor_ID As String = Get_Motherboard_ID()
    ' MsgBox(Get_CPU_ID())
 
    Private Function Get_CPU_ID() As String
        For Each CPU_ID As Object In GetObject("winmgmts:{impersonationLevel=impersonate}!\\.\root\cimv2").ExecQuery("Select * from Win32_Processor") : Return CPU_ID.ProcessorId : Next CPU_ID
        Return Nothing
    End Function
 
#End Region

``` 