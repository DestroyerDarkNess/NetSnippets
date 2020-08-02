###  Get the directory or file path "user.config"


```vb
 
#Region " Get User Config Function "
 
    ' [ Get User Config Function ]
    '
    ' // By Elektro H@cker (Gracias a Seba123Neo)
    '
    ' Examples :
    ' 
    ' * First add a reference to "System.Configuration" in the proyect
    '
    ' MsgBox(Get_User_Config(User_Config.File))
    ' MsgBox(Get_User_Config(User_Config.Path))
 
    Enum User_Config
        File
        Path
    End Enum
 
    Private Function Get_User_Config(ByVal Setting As User_Config) As String
        Dim UserConfig As String = System.Configuration.ConfigurationManager.OpenExeConfiguration(System.Configuration.ConfigurationUserLevel.PerUserRoaming).FilePath
        Select Case Setting
            Case User_Config.File : Return UserConfig
            Case User_Config.Path : Return UserConfig.Substring(0, UserConfig.LastIndexOf("\"))
            Case Else : Return False
        End Select
    End Function
 
#End Region

``` 