### To change Windows cursors (On the system, outside the form)


```vb
 
#Region " Set System Cursor Function "
 
    ' [ Set System Cursor Function ]
    '
    ' Examples :
    '
    ' Set_System_Cursor("C:\Cursors\Arrow.ani", System_Cursor.ARROW))
    ' MsgBox(Set_System_Cursor("C:\Cursors\Cross.cur", System_Cursor.CROSS))
 
    ' Set System Cursor [ API declarations ]
    Private Declare Function SetSystemCursor Lib "user32.dll" (ByVal hCursor As IntPtr, ByVal id As Integer) As Boolean
    Private Declare Function LoadCursorFromFile Lib "user32.dll" Alias "LoadCursorFromFileA" (ByVal lpFileName As String) As IntPtr
 
    ' Set System Cursor [ API Constants ]
    Private Enum System_Cursor As UInt32
        APP_STARTING = 32650
        ARROW = 32512
        CROSS = 32515
        HAND = 32649
        HELP = 32651
        I_BEAM = 32513
        NO = 32648
        SIZE_ALL = 32646
        SIZE_NESW = 32643
        SIZE_NS = 32645
        SIZE_NWSE = 32642
        SIZE_WE = 32644
        UP = 32516
        WAIT = 32514
    End Enum
 
    ' Set System Cursor [ Function ]
    Private Function Set_System_Cursor(ByVal Cursor_File As String, ByVal Cursor_Type As System_Cursor) As Boolean
        If SetSystemCursor(LoadCursorFromFile(Cursor_File), Cursor_Type) = 0 Then Return False ' Error loading cursor from file
        Return True
    End Function
 
#End Region

``` 