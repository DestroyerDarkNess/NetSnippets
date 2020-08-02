###  local Day:


```vb

 Dim Today as string = My.Computer.Clock.LocalTime.DayOfWeek ' In English language
 
 Dim Today as string = System.Globalization.DateTimeFormatInfo.CurrentInfo.GetDayName(Date.Today.DayOfWeek) ' In system language

``` 