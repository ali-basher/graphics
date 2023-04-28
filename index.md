# Graphics

## 1- Draw Line by DDA in Form

---
![Draw Line by DDA in Form](img/DDA%20in%20Form.png)
![Draw Line by DDA in Form](img/DDA%20in%20Form%202.png)

```vbnet
Public Class Form1
    Dim i As Integer
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        Dim x1 As Integer, y1 As Integer
        Dim x2 As Integer, y2 As Integer

        x1 = TextBox1.Text
        y1 = TextBox2.Text
        x2 = TextBox3.Text
        y2 = TextBox4.Text

        dda(x1, y1, x2, y2)

    End Sub

    Public Sub dda(x1 As Integer, y1 As Integer, x2 As Integer, y2 As Integer)
        Dim length As Integer
        Dim dx As Double, dy As Double
        Dim x As Integer, y As Integer
        Dim x_temp = x
        Dim y_temp = y

        Dim g As Graphics = Me.CreateGraphics()
        Dim mypen As New Pen(Color.Black, 2)

        If Math.Abs(x2 - x1) > Math.Abs(y2 - y1) Then
            length = Math.Abs(x2 - x1)
        Else
            length = Math.Abs(y2 - y1)
        End If

        dx = (x2 - x1) / length
        dy = (y2 - y1) / length

        x = x1 + 0.5 * sign_fun(x2 - x1)
        y = y1 + 0.5 * sign_fun(y2 - y1)
        x_temp = x
        y_temp = y
        For Me.i = 1 To length
            x = x + dx
            y = y + dy
            g.DrawLine(mypen, CInt(x_temp), CInt(y_temp), CInt(x), CInt(y))

            x_temp = x
            y_temp = y
        Next
    End Sub

    Public Function sign_fun(ByRef d As Integer) As Integer
        Dim k As Integer
        If d > 0 Then k = 1
        If d = 0 Then k = 0
        If d < 0 Then k = -1

        sign_fun = k
    End Function

End Class

```

---
