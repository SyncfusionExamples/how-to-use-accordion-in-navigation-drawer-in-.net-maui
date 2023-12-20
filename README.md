# how-to-use-accordion-in-navigation-drawer-in-.net-maui
This example demonstrates about how to use Accordion (SfAccordion) in SfNavigationDrawer in .NET MAUI.

You can load the [SfAccordion](https://www.syncfusion.com/maui-controls/maui-accordion) to the [SfNavigationDrawer](https://www.syncfusion.com/maui-controls/maui-NavigationDrawer) in [.NET MAUI Accordion](https://www.syncfusion.com/maui-controls/maui-accordion).

**XAML**
Load the [SfAccordion](https://www.syncfusion.com/maui-controls/maui-accordion) into the [SfNavigationDrawer.DrawerContentView](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.SfNavigationDrawer.html#Syncfusion_Maui_NavigationDrawer_SfNavigationDrawer_ContentView) . Add hamburger icon to the Image with Image.GestureRecognizer and bind the ViewModel command to the TapGestureRecognizer.Command to toggle the drawer.

``` xml
<navigationdrawer:SfNavigationDrawer x:Name="navigationDrawer">
            
    <navigationdrawer:SfNavigationDrawer.ContentView>
        <Grid x:Name="mainContentView" BackgroundColor="White">
            <Grid.RowDefinitions>
                <RowDefinition Height="auto"/>
                <RowDefinition/>
            </Grid.RowDefinitions>
            <Grid BackgroundColor="#e8e8e8" >
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="50"/>
                    <ColumnDefinition Width="*"/>
                </Grid.ColumnDefinitions>
                <Image x:Name="hamburgerButton" Source="hamburger.png" HeightRequest="30" WidthRequest="30" Margin="5,0,0,0" HorizontalOptions="Start">
                    <Image.GestureRecognizers>
                        <TapGestureRecognizer Command="{Binding ToggleDrawerCommand}" CommandParameter="{x:Reference navigationDrawer}"/>
                    </Image.GestureRecognizers>
                </Image>
                <Label x:Name="headerLabel" Grid.Column="1" HeightRequest="50" HorizontalTextAlignment="Start" VerticalTextAlignment="Center" Text="Home" FontSize="16" TextColor="#385170" />
            </Grid>
            <Label Grid.Row="1" x:Name="contentLabel" VerticalOptions="Center" HorizontalOptions="Center" Text="Content View" FontSize="14"/>
        </Grid>
    </navigationdrawer:SfNavigationDrawer.ContentView>
            
    <navigationdrawer:SfNavigationDrawer.DrawerSettings>
        <navigationdrawer:DrawerSettings DrawerHeaderHeight="160" DrawerFooterHeight="0">
                    
            <navigationdrawer:DrawerSettings.DrawerHeaderView>
                <Grid BackgroundColor="Black">
                    <Image Source="burger.jpg" HeightRequest="110" Margin="0,10,0,0" VerticalOptions="Center" HorizontalOptions="Center" />
                </Grid>
            </navigationdrawer:DrawerSettings.DrawerHeaderView>
                    
            <navigationdrawer:DrawerSettings.DrawerContentView>
                <Grid BackgroundColor="#323f4c">                          
                        <accordion:SfAccordion x:Name="accordion"  BindableLayout.ItemsSource="{Binding Info}"  ExpandMode="SingleOrNone" HeaderIconPosition="End">
                            <BindableLayout.ItemTemplate>
                                <DataTemplate>
                                    <accordion:AccordionItem HeaderBackground="#1f2933" HeaderIconColor="#cbd2d9">
                                        <accordion:AccordionItem.Header>
                                            <Grid>
                                                <Label Text="{Binding Name}" VerticalOptions="Center" HorizontalOptions="StartAndExpand" HeightRequest="50" TextColor="#cbd2d9" Padding="5,0,0,0" VerticalTextAlignment="Center"/>
                                            </Grid>
                                        </accordion:AccordionItem.Header>
                                        <accordion:AccordionItem.Content>
                                            <Grid Padding="5,0,5,0" BackgroundColor="#3e4c59">
                                                <Label Text="{Binding Description}" TextColor="#cbd2d9" VerticalOptions="Center"/>
                                            </Grid>
                                        </accordion:AccordionItem.Content>
                                    </accordion:AccordionItem>
                                </DataTemplate>
                            </BindableLayout.ItemTemplate>
                        </accordion:SfAccordion>                           
                </Grid>
            </navigationdrawer:DrawerSettings.DrawerContentView>
        </navigationdrawer:DrawerSettings>               
    </navigationdrawer:SfNavigationDrawer.DrawerSettings>                    
</navigationdrawer:SfNavigationDrawer>
```

**C#**

[ToggleDrawer()](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.SfNavigationDrawer.html#Syncfusion_Maui_NavigationDrawer_SfNavigationDrawer_ToggleDrawer) for navigation drawer in the command execution method.

``` c#
public class ItemInfoRepository : INotifyPropertyChanged
{		
   public Command ToggleDrawerCommand { get; set; }
   public ItemInfoRepository()
   {
     ToggleDrawerCommand = new Command(OpenDrawer);
   }
   private void OpenDrawer(object obj)
   {
     (obj as SfNavigationDrawer).ToggleDrawer();
   }
}

```

[View sample in GitHub](https://github.com/SyncfusionExamples/how-to-use-accordion-in-navigation-drawer-in-.net-maui)

**Conclusion**
I hope you enjoyed learning about how to use [SfAccordion](https://www.syncfusion.com/maui-controls/maui-accordion) in [SfNavigationDrawer](https://www.syncfusion.com/maui-controls/maui-NavigationDrawer) in .NET MAUI .
You can refer to our [.NET MAUI Accordion](https://www.syncfusion.com/maui-controls/maui-accordion) feature tour page to know about its other groundbreaking feature representations and [documentation](https://help.syncfusion.com/maui/expander/getting-started), and how to quickly get started for configuration specifications. You can also explore our .NET MAUI Expander [example](https://github.com/syncfusion/maui-demos/tree/master/MAUI/Accordion) to understand how to create and manipulate data.
For current customers, you can check out our components from the License and Downloads page. If you are new to Syncfusion, you can try our 30-day [free trial](https://www.syncfusion.com/downloads/maui) to check out our other controls.
If you have any queries or require clarifications, please let us know in the comments section below. You can also contact us through our [support forums](https://www.syncfusion.com/forums/), [Direct-Trac](https://support.syncfusion.com/create), or [feedback portal](https://www.syncfusion.com/feedback/maui?control=sflistview). We are always happy to assist you!