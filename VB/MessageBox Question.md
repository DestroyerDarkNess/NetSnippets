### MessageBox Question - Cancel operation


```vb
 
Dim Answer = MessageBox.Show("Want to cancel the current operation?", "Cancel", MessageBoxButtons.YesNo, MessageBoxIcon.Question, MessageBoxDefaultButton.Button1)
  If Answer = MsgBoxResult.Yes Then Application.Exit() Else e.Cancel = True

``` 