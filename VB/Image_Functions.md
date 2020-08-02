### Image Functions
 
 -load an image in a certain resolution:


```vb
 
Public Function read_image_at_res(ByRef file As String, ByRef force_sizex As Integer, ByRef force_sizey As Integer) As System.Drawing.Bitmap
        Dim img As New Bitmap(file)
        Dim b As New Bitmap(force_sizex, force_sizey)
        Dim bg As Graphics = Graphics.FromImage(b)
        Try
            bg.DrawImage(img, New Rectangle(New Point(0, 0), New Size(force_sizex, force_sizey)), New Rectangle(0, 0, img.Width, img.Height), GraphicsUnit.Pixel)
        Catch ex As Exception
 
        End Try
        bg.Dispose()
        Return b
    End Function

``` 

-resize an image:

```vb
 
Public Function resize_bmp(ByRef img As Bitmap, ByRef sizex As Integer, ByRef sizey As Integer) As Bitmap
        Dim b As New Bitmap(sizex, sizey)
        Dim bg As Graphics = Graphics.FromImage(b)
        bg.DrawImage(img, New Rectangle(New Point(0, 0), New Size(sizex, sizey)), New Rectangle(0, 0, img.Width, img.Height), GraphicsUnit.Pixel)
        bg.Dispose()
        Return b
    End Function

``` 

-superimpose two images on one canvas:

```vb
 
Public Function layer_sum(ByRef layer1 As Bitmap, ByRef layer2 As Bitmap) As Bitmap
        Dim bg As Graphics = Graphics.FromImage(layer1)
        bg.DrawImage(layer2, New Point(0, 0))
        bg.Dispose()
        Return layer1
End Function

``` 

-write plain text (with rudimentary shading) on a transparent background:

```vb
 
 Public Function get_text_layer(ByRef size As System.Drawing.Size, ByRef text As String) As System.Drawing.Bitmap
        Dim img As New Bitmap(size.Width, size.Height)
        Dim bg As Graphics = Graphics.FromImage(img)
        bg.DrawString(text, New Font("Lucida Console", 12, FontStyle.Bold), Brushes.Gray, New Point(1, -1))
        bg.DrawString(text, New Font("Lucida Console", 12, FontStyle.Bold), Brushes.White, New Point(0, 0))
        bg.Dispose()
        Return img
    End Function

``` 

-divide the image into sectors and return the one indicated by "index":

```vb
 
  Public Function get_portion(ByRef image As System.Drawing.Bitmap, ByRef cuadriculax As Short, ByRef cuadriculay As Short, ByRef index As Integer) As System.Drawing.Bitmap
        Dim img As New Bitmap(CInt(image.Size.Width / cuadriculax), CInt(image.Size.Height / cuadriculay))
        'Dim b As New Bitmap(CInt(image.Size.Width / cuadriculax), CInt(image.Size.Height / cuadriculay))
        Dim bg As Graphics = Graphics.FromImage(img)
        Dim xcount = 0
        Dim ycount = 0
        Do While index >= cuadriculax
            index = index - cuadriculax
            ycount = ycount + 1
        Loop
        xcount = index
        Dim tmpx As Integer = CInt((image.Size.Width / cuadriculax) * xcount)
        Dim tmpy As Integer = CInt((image.Size.Height / cuadriculay) * ycount)
        Dim port As New Rectangle(New System.Drawing.Point(0, 0), New Size(New Point(CInt(image.Size.Width / cuadriculax), CInt(image.Size.Height / cuadriculay))))
        bg.DrawImage(image, port, tmpx, tmpy, CInt(port.Size.Width), CInt(port.Size.Height), GraphicsUnit.Pixel)
        bg.Dispose()
        Return img
    End Function

``` 

