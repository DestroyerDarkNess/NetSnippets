-Center a child form on the parent form:

```vb
       #Region " CenterForm function "
 
    Function CenterForm(ByVal Form_to_Center As Form, ByVal Form_Location As Point) As Point
        Dim FormLocation As New Point
        FormLocation.X = (Me.Left + (Me.Width - Form_to_Center.Width) / 2) ' set the X coordinates.
        FormLocation.Y = (Me.Top + (Me.Height - Form_to_Center.Height) / 2) ' set the Y coordinates.
        Return FormLocation ' return the Location to the Form it was called from.
    End Function
 
#End Region
 
    ' Form2 Load
    Private Sub Form2_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        Me.Location = Form1.centerForm(Me, Me.Location)
    End Sub
 
    ' Private Sub Button_MouseHover(sender As Object, e As EventArgs) Handles Button1.MouseHover
    '     Form2.Show()
    ' End Sub
 
    ' Private Sub Button_MouseLeave(sender As Object, e As EventArgs) Handles Button1.MouseLeave
    '     Form2.Dispose()
    ' End Sub
``` 
