-Process all image files from My.Resources:


```vb
          For Each ResourceFile As DictionaryEntry In My.Resources.ResourceManager.GetResourceSet(Globalization.CultureInfo.CurrentCulture, True, True).OfType(Of Object)()
            If TypeOf (ResourceFile.Value) Is Drawing.Image Then
                Button_2000_2006.Image = ResourceFile.Value
                'MsgBox(ResourceFile.Key)   ' Resource Name
                'MsgBox(ResourceFile.Value) ' Resource FileContent
            End If
        Next
``` 