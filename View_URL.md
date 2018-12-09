# Software
Public Class Form2
Private Sub DataGridView1_CellContentClick(sender As Object, e As
DataGridViewCellEventArgs) Handles DataGridView1.CellContentClick
DataGridView1.DataSource = GetURLList()
End Sub
Private Function GetURLList() As DataTable
Dim dtURL As New DataTable
Return dtURL
2) Write code in the web application configuration in order to make database connection with the
registered ‘OLEDB’ provider as follows:
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
<configSections>
</configSections>
<connectionStrings>
<add
name="WindowsApplication2.My.MySettings.FF142PC016ConnectionString"
connectionString="Data
Source=(LocalDB)\v11.0;AttachDbFilename=|DataDirectory|\FF142PC01
6.mdf;Integrated Security=True;Connect Timeout=30"
providerName="System.Data.SqlClient" />
</connectionStrings>
<startup>
<supportedRuntime version="v4.0"
sku=".NETFramework,Version=v4.5" />
</startup>
<connectionStrings>
<add name="db" connectionString=""
providerName="System.Data.OleDb"/>
</connectionStrings>
</configuration>
