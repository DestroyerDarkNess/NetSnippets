- An example of a SaveFileDialog:

```vb
Dim SaveFile As New SaveFileDialog
         SaveFile.Title = "Save a Report File"
         SaveFile.InitialDirectory = Environ ("programfiles")
         SaveFile.RestoreDirectory = True
         SaveFile.DefaultExt = "txt"
         SaveFile.Filter = "txt file (* .txt) | * .txt"
         SaveFile.CheckPathExists = True
         SaveFile.CheckFileExists = True
         SaveFile.ShowDialog ()
 
         If SaveFile.ShowDialog () = DialogResult.OK Then
           MsgBox (SaveFile.FileName)
         End If
``` 