-link label Sample

```vb
      ' First add a LinkLabel control into the form.
 
    Private Sub LinkLabel_LinkClicked(sender As Object, e As LinkLabelLinkClickedEventArgs) Handles LinkLabel1.LinkClicked
        System.Diagnostics.Process.Start("http://www.Google.com")
        System.Diagnostics.Process.Start("mailto:ME@Hotmail.com")
    End Sub
``` 