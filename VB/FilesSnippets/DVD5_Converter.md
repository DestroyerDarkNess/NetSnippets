-For an application I needed to divide the size of a few MEgaBytes by the capacity of a DVD5, so now I have made this snippet that divides the size between several disk formats, for the next occasion.

*The measurements are taken from Wikipedia, for the most ...

```vb
        
    ' Usage:
    '
    ' MsgBox(ConvertToDiscSize(737280000, "Bytes", "CD"))
    ' MsgBox(ConvertToDiscSize(700, "MB", "CD"))
    ' MsgBox(Math.Ceiling(ConvertToDiscSize(6.5, "GB", "DVD")))
    ' MsgBox(ConvertToDiscSize(40, "GB", "BR").ToString.Substring(0, 3) & " Discs")
 
#Region " Convert To Disc Size function"
    Private Function ConvertToDiscSize(ByVal FileSize As Double, ByVal FileKindSize As String, ByVal To_DiscKindCapacity As String)
 
        ' KindSize Measures:
        ' --------------------------
        ' Bytes
        ' KB
        ' MB
        ' GB
 
        ' ToDiscKind Measures:
        ' -----------------------------
        ' CD
        ' CD800
        ' CD900
        ' DVD
        ' DVD-DL
        ' BR
        ' BR-DL
        ' BR-3L
        ' BR-4L
        ' BR-MD
        ' BR-MD-DL
 
 
        ' Bytes
        If FileKindSize.ToUpper = "BYTES" Then
            If To_DiscKindCapacity.ToUpper = "CD" Then Return FileSize / 737280000 ' CD Standard
            If To_DiscKindCapacity.ToUpper = "CD800" Then Return FileSize / 829440393.216 ' CD 800 MB
            If To_DiscKindCapacity.ToUpper = "CD900" Then Return FileSize / 912383803.392 ' CD 900 MB
            If To_DiscKindCapacity.ToUpper = "DVD" Then Return FileSize / 4700000000 ' DVD Standard (DVD5
            If To_DiscKindCapacity.ToUpper = "DVD-DL" Then Return FileSize / 8500000000 ' DVD Double Layer (DVD9)
            If To_DiscKindCapacity.ToUpper = "BR" Then Return FileSize / 25025314816 ' BluRay Standard
            If To_DiscKindCapacity.ToUpper = "BR-DL" Then Return FileSize / 50050629632 ' BluRay Double Layer
            If To_DiscKindCapacity.ToUpper = "BR-3L" Then Return FileSize / 100103356416 ' BluRay x3 Layers
            If To_DiscKindCapacity.ToUpper = "BR-4L" Then Return FileSize / 128001769472 ' BluRay x4 Layers
            If To_DiscKindCapacity.ToUpper = "BR-MD" Then Return FileSize / 7791181824 ' BluRay MiniDisc Standard
            If To_DiscKindCapacity.ToUpper = "BR-MD-DL" Then Return FileSize / 15582363648 ' BluRay MiniDisc Double Layer
 
            ' KB
        ElseIf FileKindSize.ToUpper = "KB" Then
            If To_DiscKindCapacity.ToUpper = "CD" Then Return FileSize / 720000 ' CD Standard
            If To_DiscKindCapacity.ToUpper = "CD800" Then Return FileSize / 810000.384 ' CD 800 MB
            If To_DiscKindCapacity.ToUpper = "CD900" Then Return FileSize / 890999.808 ' CD 900 MB
            If To_DiscKindCapacity.ToUpper = "DVD" Then Return FileSize / 4589843.75 ' DVD Standard (DVD5)
            If To_DiscKindCapacity.ToUpper = "DVD-DL" Then Return FileSize / 8300781.25 ' DVD Double Layer (DVD9)
            If To_DiscKindCapacity.ToUpper = "BR" Then Return FileSize / 24438784 ' BluRay Standard
            If To_DiscKindCapacity.ToUpper = "BR-DL" Then Return FileSize / 48877568 ' BluRay Double Layer
            If To_DiscKindCapacity.ToUpper = "BR-3L" Then Return FileSize / 97757184 ' BluRay x3 Layers
            If To_DiscKindCapacity.ToUpper = "BR-4L" Then Return FileSize / 125001728 ' BluRay x4 Layers
            If To_DiscKindCapacity.ToUpper = "BR-MD" Then Return FileSize / 7608576 ' BluRay MiniDisc Standard
            If To_DiscKindCapacity.ToUpper = "BR-MD-DL" Then Return FileSize / 15217152 ' BluRay MiniDisc Double Layer
 
            ' MB
        ElseIf FileKindSize.ToUpper = "MB" Then
            If To_DiscKindCapacity.ToUpper = "CD" Then Return FileSize / 703.125 ' CD Standard
            If To_DiscKindCapacity.ToUpper = "CD800" Then Return FileSize / 791.016 ' CD 800 MB
            If To_DiscKindCapacity.ToUpper = "CD900" Then Return FileSize / 870.117 ' CD 900 MB
            If To_DiscKindCapacity.ToUpper = "DVD" Then Return FileSize / 4482.26929 ' DVD Standard (DVD5)
            If To_DiscKindCapacity.ToUpper = "DVD-DL" Then Return FileSize / 8106.23169 ' DVD Double Layer (DVD9)
            If To_DiscKindCapacity.ToUpper = "BR" Then Return FileSize / 23866 ' BluRay Standard
            If To_DiscKindCapacity.ToUpper = "BR-DL" Then Return FileSize / 47732 ' BluRay Double Layer
            If To_DiscKindCapacity.ToUpper = "BR-3L" Then Return FileSize / 95466 ' BluRay x3 Layers
            If To_DiscKindCapacity.ToUpper = "BR-4L" Then Return FileSize / 122072 ' BluRay x4 Layers
            If To_DiscKindCapacity.ToUpper = "BR-MD" Then Return FileSize / 7430.25 ' BluRay MiniDisc Standard
            If To_DiscKindCapacity.ToUpper = "BR-MD-DL" Then Return FileSize / 14860.5 ' BluRay MiniDisc Double Layer
 
            ' GB
        ElseIf FileKindSize.ToUpper = "GB" Then
            If To_DiscKindCapacity.ToUpper = "CD" Then Return FileSize / 0.68665 ' CD Standard
            If To_DiscKindCapacity.ToUpper = "CD800" Then Return FileSize / 0.77248 ' CD 800 MB
            If To_DiscKindCapacity.ToUpper = "CD900" Then Return FileSize / 0.84972 ' CD 900 MB
            If To_DiscKindCapacity.ToUpper = "DVD" Then Return FileSize / 4.37722 ' DVD Standard (DVD5)
            If To_DiscKindCapacity.ToUpper = "DVD-DL" Then Return FileSize / 7.91624 ' DVD Double Layer (DVD9)
            If To_DiscKindCapacity.ToUpper = "BR" Then Return FileSize / 23.30664 ' BluRay Standard
            If To_DiscKindCapacity.ToUpper = "BR-DL" Then Return FileSize / 46.61328 ' BluRay Double Layer
            If To_DiscKindCapacity.ToUpper = "BR-3L" Then Return FileSize / 93.22852 ' BluRay x3 Layers
            If To_DiscKindCapacity.ToUpper = "BR-4L" Then Return FileSize / 119.21094 ' BluRay x4 Layers
            If To_DiscKindCapacity.ToUpper = "BR-MD" Then Return FileSize / 7.2561 ' BluRay MiniDisc Standard
            If To_DiscKindCapacity.ToUpper = "BR-MD-DL" Then Return FileSize / 14.51221 ' BluRay MiniDisc Double Layer
        End If
 
        Return Nothing ' Argument measure not found
 
    End Function
#End Region

``` 