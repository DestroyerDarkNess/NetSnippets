-Sort a listview by clicking on the column to sort:

```vb
' Instructions:
' 1. Add the class
' 2. Add the declaration
' 3. Add a listview
 
 
Dim ColumnOrder As String = "Down"
 
 
#Region " ListView Sort Column event "
 
    Private Sub ListView_ColumnClick(ByVal sender As Object, ByVal e As System.Windows.Forms.ColumnClickEventArgs) Handles ListView1.ColumnClick
        If ColumnOrder = "Down" Then
            Me.ListView1.ListViewItemSorter = New OrdenarListview(e.Column, SortOrder.Ascending)
            ListView1.Sort()
            ColumnOrder = "Up"
        ElseIf ColumnOrder = "Up" Then
            Me.ListView1.ListViewItemSorter = New OrdenarListview(e.Column, SortOrder.Descending)
            ListView1.Sort()
            ColumnOrder = "Down"
        End If
    End Sub
 
 
#End Region
 
 
#Region " OrdenarListView [CLASS] "
 
Public Class OrdenarListview
    Implements IComparer
 
    Private vIndiceColumna As Integer
    Private vTipoOrden As SortOrder
 
    Public Sub New(ByVal pIndiceColumna As Integer, ByVal pTipoOrden As SortOrder)
        vIndiceColumna = pIndiceColumna
        vTipoOrden = pTipoOrden
    End Sub
 
    Public Function Ordenar(ByVal x As Object, ByVal y As Object) As Integer Implements System.Collections.IComparer.Compare
        Dim item_x As ListViewItem = DirectCast(x, ListViewItem)
        Dim item_y As ListViewItem = DirectCast(y, ListViewItem)
 
        Dim string_x As String
 
        If item_x.SubItems.Count <= vIndiceColumna Then
            string_x = ""
        Else
            string_x = item_x.SubItems(vIndiceColumna).Text
        End If
 
        Dim string_y As String
        If item_y.SubItems.Count <= vIndiceColumna Then
            string_y = ""
        Else
            string_y = item_y.SubItems(vIndiceColumna).Text
        End If
 
        If vTipoOrden = SortOrder.Ascending Then
            If IsNumeric(string_x) And IsNumeric(string_y) Then
                Return Val(string_x).CompareTo(Val(string_y))
            ElseIf IsDate(string_x) And IsDate(string_y) Then
                Return DateTime.Parse(string_x).CompareTo(DateTime.Parse(string_y))
            Else
                Return String.Compare(string_x, string_y)
            End If
        Else
            If IsNumeric(string_x) And IsNumeric(string_y) Then
                Return Val(string_y).CompareTo(Val(string_x))
            ElseIf IsDate(string_x) And IsDate(string_y) Then
                Return DateTime.Parse(string_y).CompareTo(DateTime.Parse(string_x))
            Else
                Return String.Compare(string_y, string_x)
            End If
        End If
    End Function
End Class
 
#End Region

```