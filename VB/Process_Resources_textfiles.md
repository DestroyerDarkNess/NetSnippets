-Process all My.Resources text files:

```vb
         For Each ResourceFile As DictionaryEntry In My.Resources.ResourceManager.GetResourceSet(Globalization.CultureInfo.CurrentCulture, True, True).OfType(Of Object)()
            If TypeOf (ResourceFile.Value) Is String Then
                MsgBox(My.Resources.ResourceManager.GetObject(ResourceFile.Key))
                'MsgBox(ResourceFile.Key)   ' Resource Name
                'MsgBox(ResourceFile.Value) ' Resource FileContent
            End If
        Next
``` 