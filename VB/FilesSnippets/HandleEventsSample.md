
-Handle the same event for multiple controls:

```vb
    Private Sub Button_Is_Clicked(sender As Object, e As EventArgs) Handles _
        Button1.Click, _
        Button2.Click, _
        Button3.Click
 
        Dim Clicked_Button As Button = CType(sender, Button)
 
        If Clicked_Button.Name = "Button1" Then
        ' Things for Button1
        ElseIf Clicked_Button.Name = "Button2" Then
        ' Things for Button2
        ElseIf Clicked_Button.Name = "Button3" Then
        ' Things for Button3
        End If
    Ens Sub
``` 