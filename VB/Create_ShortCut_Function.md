### Create a shortcut to an application or a web page, with many options.


```vb
 
#Region " Create ShortCut Function "
 
    ' [ Create ShortCut Function ]
    '
    ' // By Elektro H@cker
    '
    ' Examples :
    '
    ' Create_ShortCut(ShortcutPath.MyDocuments, "My APP Shortcut.lnk", "C:\File.exe")
    ' Create_ShortCut(ShortcutPath.Desktop, "My CMD Shortcut.lnk", "CMD.exe", "/C Echo Hello World & Pause")
    ' Create_ShortCut(ShortcutPath.Favorites, "My INTERNET Shortcut.lnk", "http://www.Google.com", , "CTRL+SHIFT+S")
    ' Create_ShortCut(ShortcutPath.Favorites, "My INTERNET Shortcut.lnk", "http://www.Google.com", , "CTRL+SHIFT+S", "Description of the shortcut")
 
    Enum ShortcutPath
        AppData = Environment.SpecialFolder.ApplicationData
        Desktop = Environment.SpecialFolder.Desktop
        Favorites = Environment.SpecialFolder.Favorites
        LocalAppData = Environment.SpecialFolder.LocalApplicationData
        MyDocuments = Environment.SpecialFolder.MyDocuments
        ProgramFiles = Environment.SpecialFolder.ProgramFiles
        ProgramFilesx86 = Environment.SpecialFolder.ProgramFilesX86
        StartMenu = Environment.SpecialFolder.StartMenu
        System32 = Environment.SpecialFolder.System
        SysWOW64 = Environment.SpecialFolder.SystemX86
        UserProfile = Environment.SpecialFolder.UserProfile
        Windows = Environment.SpecialFolder.Windows
    End Enum
 
    Function Create_ShortCut(ByVal Shortcut_Path As ShortcutPath, _
                            ByVal Shortcut_Name As String, _
                            ByVal APP As String, _
                            Optional ByVal APP_Arguments As String = Nothing, _
                            Optional ByVal HotKey As String = Nothing, _
                            Optional ByVal Icon As String = Nothing, _
                            Optional ByVal Description As String = Nothing) As Boolean
 
        Dim Dir = New IO.DirectoryInfo(System.Environment.GetFolderPath(Shortcut_Path))
        Dim WorkingDir As IO.FileInfo
        If Not APP.Contains("/") Then WorkingDir = New IO.FileInfo(APP) Else WorkingDir = Nothing
        Try
            Dim WSHShell As Object = CreateObject("WScript.Shell")
            Dim Shortcut As Object
            Shortcut = WSHShell.CreateShortcut(Dir.FullName & "\" & Shortcut_Name)
            Shortcut.TargetPath = APP
            Shortcut.Arguments = APP_Arguments
            Shortcut.WindowStyle = 2
            Shortcut.Hotkey = HotKey
            Shortcut.Description = Description
            If Not APP.Contains("/") Then Shortcut.WorkingDirectory = WorkingDir.DirectoryName
            If Icon IsNot Nothing Then Shortcut.IconLocation = Icon Else Shortcut.IconLocation = APP
            Shortcut.Save()
            Return True
        Catch ex As Exception
            Return False
        End Try
    End Function
 
#End Region

``` 