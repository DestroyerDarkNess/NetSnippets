-Another converter, this time a converter of time, ms, seconds, minutes, hours.

```vb
        
#Region " Convert Time Function"
 
    ' // By Elektro H@cker
    '
    ' MsgBox(Convert_Time(1, "h", "m"))
    ' MsgBox(Convert_Time(1, "h", "s"))
    ' MsgBox(Convert_Time(1, "h", "ms"))
    ' MsgBox(Convert_Time(6000, "milliseconds", "seconds"))
    ' MsgBox(Convert_Time(6000, "seconds", "minutes"))
    ' MsgBox(Convert_Time(6000, "minutes", "hours"))
 
    Private Function Convert_Time(ByVal Time As Int64, ByVal Input_Time_Format As String, ByVal Output_Time_Format As String)
        Dim Time_Span As New TimeSpan
        If Input_Time_Format.ToUpper = "MS" Or Output_Time_Format.ToUpper = "MILLISECONDS" Then Time_Span = New TimeSpan(TimeSpan.TicksPerMillisecond * Time)
        If Input_Time_Format.ToUpper = "S" Or Output_Time_Format.ToUpper = "SECONDS" Then Time_Span = New TimeSpan(TimeSpan.TicksPerSecond * Time)
        If Input_Time_Format.ToUpper = "M" Or Output_Time_Format.ToUpper = "MINUTES" Then Time_Span = New TimeSpan(TimeSpan.TicksPerMinute * Time)
        If Input_Time_Format.ToUpper = "H" Or Output_Time_Format.ToUpper = "HOURS" Then Time_Span = New TimeSpan(TimeSpan.TicksPerHour * Time)
        If Output_Time_Format.ToUpper = "MS" Or Output_Time_Format.ToUpper = "MILLISECONDS" Then Return Time_Span.TotalMilliseconds
        If Output_Time_Format.ToUpper = "S" Or Output_Time_Format.ToUpper = "SECONDS" Then Return Time_Span.TotalSeconds
        If Output_Time_Format.ToUpper = "M" Or Output_Time_Format.ToUpper = "MINUTES" Then Return Time_Span.TotalMinutes
        If Output_Time_Format.ToUpper = "H" Or Output_Time_Format.ToUpper = "HOURS" Then Return Time_Span.TotalHours
        Return False ' Returns false if argument is in incorrect format
    End Function
 
#End Region

``` 