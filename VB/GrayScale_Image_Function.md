### Darken a grayscale image (Disable image)


```vb
 
#Region " GrayScale Image Function "
 
    ' [ GrayScale Image Function ]
    '
    ' Examples:
    '
    ' PictureBox1.Image = GrayScale_Image(PictureBox1.Image, GrayScale.Light_Gray)
    ' PictureBox1.Image = GrayScale_Image(PictureBox1.Image, GrayScale.Mid_Gray)
    ' PictureBox1.Image = GrayScale_Image(PictureBox1.Image, GrayScale.Dark_Gray)
 
    Enum GrayScale
        Light_Gray
        Mid_Gray
        Dark_Gray
    End Enum
 
    Private Function GrayScale_Image(ByVal Image As Image, ByVal Gray_Tone As GrayScale) As Bitmap
        Dim Image_Bitmap As Bitmap = New Bitmap(Image.Width, Image.Height)
        Dim Image_Graphic As Graphics = Graphics.FromImage(Image_Bitmap)
        Dim Color_Matrix As System.Drawing.Imaging.ColorMatrix = Nothing
        Select Case Gray_Tone
            Case GrayScale.Light_Gray : Color_Matrix = New System.Drawing.Imaging.ColorMatrix(New Single()() {New Single() {0.2, 0.2, 0.2, 0, 0}, New Single() {0.2, 0.2, 0.2, 0, 0}, New Single() {0.5, 0.5, 0.5, 0, 0}, New Single() {0, 0, 0, 1, 0}, New Single() {0, 0, 0, 0, 1}})
            Case GrayScale.Mid_Gray : Color_Matrix = New System.Drawing.Imaging.ColorMatrix(New Single()() {New Single() {0, 0, 0, 0, 0}, New Single() {0, 0, 0, 0, 0}, New Single() {0.5, 0.5, 0.5, 0, 0}, New Single() {0, 0, 0, 1, 0}, New Single() {0, 0, 0, 0, 1}})
            Case GrayScale.Dark_Gray : Color_Matrix = New System.Drawing.Imaging.ColorMatrix(New Single()() {New Single() {0, 0, 0, 0, 0}, New Single() {0, 0, 0, 0, 0}, New Single() {0.2, 0.2, 0.2, 0, 0}, New Single() {0, 0, 0, 1, 0}, New Single() {0, 0, 0, 0, 1}})
        End Select
        Dim Image_Attributes As System.Drawing.Imaging.ImageAttributes = New System.Drawing.Imaging.ImageAttributes()
        Image_Attributes.SetColorMatrix(Color_Matrix)
        Image_Graphic.DrawImage(Image, New Rectangle(0, 0, Image.Width, Image.Height), 0, 0, Image.Width, Image.Height, GraphicsUnit.Pixel, Image_Attributes)
        Image_Graphic.Dispose()
        Return Image_Bitmap
    End Function
 
#End Region

``` 