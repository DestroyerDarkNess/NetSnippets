### Get OS architecture


```vb
 
#Region " Get OS Architecture Function "
 
    ' [ Get OS Architecture Function ]
    '
    ' // By Elektro H@cker
    '
    ' Examples :
    ' Dim Architecture = Get_OS_Architecture()
 
    Private Function Get_OS_Architecture() As Integer
        Dim Bits = Runtime.InteropServices.Marshal.SizeOf(GetType(IntPtr)) * 8
        Select Case Bits
            Case 32 : Return 32 ' x86
            Case 64 : Return 64 ' x64
            Case Else : Return Nothing ' xD
        End Select
    End Function
 
#End Region

``` 