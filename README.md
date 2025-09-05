# add-nodes-on-demand-in-bound-mode-in-.net-maui-treeview
This repository demonstrates how to dynamically add nodes on demand in bound mode using the .NET MAUI TreeView control. It provides a sample implementation that updates the TreeView by modifying the underlying data collection in the ViewModel, ensuring real-time UI updates.

## Sample

The Syncfusion® .NET MAUI TreeView allows you to add nodes at runtime in bound mode by updating the collection in the ViewModel. For the UI to reflect updates when items are added dynamically, set the NotificationSubscriptionMode property to CollectionChange.

### XAML
```xaml
<ContentPage.Content>
    <Grid RowDefinitions="50,*">
            <Button x:Name="addItem"
                    Text="Add Items"  
                    HorizontalOptions="Fill" 
                    BackgroundColor="Blue" 
                    Command="{Binding OnAddItem}"/>
            <syncfusion:SfTreeView x:Name="treeView" 
                                   Grid.Row="1"
                                   NotificationSubscriptionMode="CollectionChange,PropertyChange"  
                                   ChildPropertyName="SubFiles"
                                   ItemsSource="{Binding ImageNodeInfo}"  
                                   AutoExpandMode="AllNodesExpanded">

            <syncfusion:SfTreeView.ItemTemplate>
                <DataTemplate>
                    <Grid x:Name="grid" RowSpacing="0">
                        <Grid.ColumnDefinitions>
                              <ColumnDefinition Width="40" />
                              <ColumnDefinition Width="*" />
                        </Grid.ColumnDefinitions>
                        <Grid Grid.Column="0">
                            <Image Source="{Binding ImageIcon}"
                                   VerticalOptions="Center"
                                   HorizontalOptions="Center"
                                   HeightRequest="24" 
                                   WidthRequest="24"/>
                        </Grid>
                        <Grid Grid.Column="1">
                            <Label LineBreakMode="NoWrap"
                                   Text="{Binding ItemName}"
                                   VerticalTextAlignment="Center">
                            </Label>
                        </Grid>
                    </Grid>
                </DataTemplate>
            </syncfusion:SfTreeView.ItemTemplate>
        </syncfusion:SfTreeView>
    </Grid>
</ContentPage.Content>
```

### ViewModel
```csharp
public class FileManagerViewModel
{
    public Command OnAddItem { get; set; }
 
    public FileManagerViewModel()
    {
        GenerateSource();
        OnAddItem = new Command(OnAddItemMethod);
    }
    private void OnAddItemMethod(object obj)
    {
        var game = new FileManager() { ItemName = "Game", ImageIcon = "game.png"};
        var games = new FileManager() { ItemName = "Criket.exe", ImageIcon = "cricket.png" };
        game.SubFiles = new ObservableCollection<FileManager>
        {
            games
        };
        ImageNodeInfo!.Add(game);
    }
}
```

## Requirements to run the demo

To run the demo, refer to [System Requirements for .NET MAUI](https://help.syncfusion.com/maui/system-requirements).

## Troubleshooting:
### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.

## License

Syncfusion® has no liability for any damage or consequence that may arise from using or viewing the samples. The samples are for demonstrative purposes. If you choose to use or access the samples, you agree to not hold Syncfusion® liable, in any form, for any damage related to use, for accessing, or viewing the samples. By accessing, viewing, or seeing the samples, you acknowledge and agree Syncfusion®'s samples will not allow you seek injunctive relief in any form for any claim related to the sample. If you do not agree to this, do not view, access, utilize, or otherwise do anything with Syncfusion®'s samples.

## Conclusion

I hope you enjoyed learning how to add nodes in bound mode using the .NET MAUI TreeView.

You can refer to our .NET MAUI TreeView feature tour page to know about its other groundbreaking feature representations and documentation, and how to quickly get started with configuration specifications.

You can also explore our .NET MAUI TreeView example to understand how to create and manipulate data.

You can check out our components from the License and Downloads page for current customers. If you are new to Syncfusion®, try our 30-day free trial to check out our other controls.

Please let us know in the comments section if you have any queries or require clarification. You can also contact us through our support forums, Direct-Trac, or feedback portal. We are always happy to assist you!
