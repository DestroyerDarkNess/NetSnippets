-Set_PC_State

```vb
        
    ' // By Elektro H@cker
 
    ' USAGE:
    '
    ' Set_PC_State(RESET)
    ' Set_PC_State(SUSPEND, 30, "I'm suspending your system.")
    ' Set_PC_State(LOG_OFF)
    ' Set_PC_State(HIBERN)
    ' Set_PC_State(ABORT)
 
#Region " Set PC State "
 
    Const RESET As String = " -R "
    Const SUSPEND As String = " -S "
    Const LOG_OFF As String = " -L "
    Const HIBERN As String = " -H "
    Const ABORT As String = " -A "
 
    Private Function Set_PC_State(ByVal PowerState_Action As String, Optional ByVal TimeOut As Integer = 1, Optional ByVal COMMENT As String = "")
 
        Dim Shutdown_Command As New ProcessStartInfo
        Shutdown_Command.FileName = "Shutdown.exe"
 
        Try
            If PowerState_Action = ABORT Or PowerState_Action = HIBERN Or PowerState_Action = LOG_OFF Then
                Shutdown_Command.Arguments = PowerState_Action ' Windows don't allow TimeOut or Comment options for HIBERN, LOG_OFF or ABORT actions.
            ElseIf PowerState_Action = RESET Or PowerState_Action = SUSPEND Then
                If Not COMMENT = "" Then
                    If COMMENT.Length > 512 Then COMMENT = COMMENT.Substring(0, 512) ' Only 512 chars are allowed for comment
                    Shutdown_Command.Arguments = PowerState_Action & " -T " & TimeOut & " /C " & COMMENT
                Else
                    Shutdown_Command.Arguments = PowerState_Action & " -T " & TimeOut
                End If
                Shutdown_Command.WindowStyle = ProcessWindowStyle.Hidden
                Process.Start(Shutdown_Command)
                Return True
            End If
        Catch ex As Exception
            Return ex.Message
        End Try
 
        Return Nothing ' Invalid argument
    End Function
 
#End Region

``` 