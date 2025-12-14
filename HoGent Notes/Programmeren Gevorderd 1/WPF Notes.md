# Grid
```csharp
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="auto"/>
        <RowDefinition Height="*"/>
        <RowDefinition Height="auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
</Grid>
```
- `Grid` -> Het gehele venster (in de eerste instantie)
- `Grid.RowDefinitions` -> Open het veld waar je de rijen gaat maken
- `RowDefinition Height`-> Stel in hoe de grootte moet zijn
	- `Height="auto"` -> Pakt *enkel* de plek die er nodig is om het element deftig te tonen
	- `Height="*"` -> Telt alle plek samen van elementen met het " * " en verdeelt de overgebleven plek *even* over de elementen

---
# DataGrid
Als je rechterklikt in een datagrid, komt er een lijst op met menuitems
```csharp
<DataGrid Grid.Row="1" Name="DataGridHRMedewerkers" Margin="5" SelectionMode="Single" IsReadOnly="True">
    <DataGrid.ContextMenu>
        <ContextMenu>
            <MenuItem Header="New" Click="MenuItemNew_Click"/>
            <MenuItem Header="Update" Click="MenuItemUpdate_Click"/>
            <MenuItem Header="Delete" Click="MenuItemDelete_Click"/>
        </ContextMenu>
    </DataGrid.ContextMenu>
</DataGrid>
```

- `SelectionMode=`
	- `Single` -> Er kan maar 1 element geselecteerd worden
	- `Extended` -> Er kunnen meerdere elementen geselecteerd worden adhv ctrl 

---

# TextBox

```csharp
<TextBox Grid.Row="0" Grid.Column="1" Margin="5" Name="TextBoxId" IsEnabled="False" Text="auto generated"/>
```
