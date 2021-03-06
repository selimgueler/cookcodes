# Xamarin Settings Page Layout Reference


| Product               | Version       | 
| -------------         |:-------------:| 
| Visual Studio 2019    | 16.7.4        | 
| Xamarin.Forms         | 4.7.0.1351    |  
  

## Define Column Definitions in AppResources

Modify the Width of ColumnDefinition as required.

```xml
<Style TargetType="Grid" x:Key="GridSettingsColumnsStyle">
                <Setter Property="Margin" Value="0,10"></Setter>
                <Setter Property="Grid.ColumnDefinitions">
                    <Setter.Value>
                        <ColumnDefinitionCollection>
                            <ColumnDefinition Width="*"></ColumnDefinition>
                            <ColumnDefinition Width="20"></ColumnDefinition>
                        </ColumnDefinitionCollection>
                    </Setter.Value>
                </Setter>
</Style>
```

## Implemention code in a Page

Example: The following should be self-explanatory. You should get the following result.

![alt-text][outputImage]

```xml

 <!--    SETTING MODULE STARTS HERE : For example: inside a StackLayout -->

        <!--    Title of Frame 1  -->
        <Label Text="More" Margin="30,0,0,0"></Label> 
        <Frame BackgroundColor="Black" Margin="20,0,20,0" CornerRadius="20" HasShadow="True">
            <StackLayout>
                <!--    Option 1 : Feedback -->
                <Grid Style="{StaticResource GridSettingsColumnsStyle}" >
                    <Grid.GestureRecognizers>
                        <TapGestureRecognizer x:Name="gridFeedback1" NumberOfTapsRequired="1" Tapped="gridFeedback1_Tapped"></TapGestureRecognizer>
                    </Grid.GestureRecognizers>
                    <Label Grid.Column="0" Text="Write Feedback"></Label>
                    <Image Grid.Column="1">
                        <Image.Source>
                            <FontImageSource Glyph="&#xf054;"
                                 FontFamily="Fontawesome"
                                 Size="10">
                            </FontImageSource>
                        </Image.Source>
                    </Image>
                </Grid>
                <!--    Seperator   -->
                <BoxView HeightRequest="1" BackgroundColor="White"></BoxView>
                <!--    Option 2 : Report a Bug -->
                <Grid Style="{StaticResource GridSettingsColumnsStyle}" >
                    <Grid.GestureRecognizers>
                        <TapGestureRecognizer x:Name="gridReportBug" NumberOfTapsRequired="1" Tapped="gridReportBug_Tapped"></TapGestureRecognizer>
                    </Grid.GestureRecognizers>
                    <Label Grid.Column="0" Text="Report a Bug"></Label>
                    <Image Grid.Column="1">
                        <Image.Source>
                            <FontImageSource Glyph="&#xf054;"
                                 FontFamily="Fontawesome"
                                 Size="10">
                            </FontImageSource>
                        </Image.Source>
                    </Image>
                </Grid>
                
                <!--    Seperator   -->
                <BoxView HeightRequest="1" BackgroundColor="White"></BoxView>
                <!--    Option 3 : About us -->
                <Grid Style="{StaticResource GridSettingsColumnsStyle}" >
                    <Grid.GestureRecognizers>
                        <TapGestureRecognizer x:Name="gridAboutUs" NumberOfTapsRequired="1" Tapped="gridAboutUs_Tapped"></TapGestureRecognizer>
                    </Grid.GestureRecognizers>
                    <Label Grid.Column="0" Text="About Us"></Label>
                    <Image Grid.Column="1">
                        <Image.Source>
                            <FontImageSource Glyph="&#xf054;"
                                 FontFamily="Fontawesome"
                                 Size="10">
                            </FontImageSource>
                        </Image.Source>
                    </Image>
                </Grid>
            </StackLayout>
            
        </Frame>
        
        <!--    ANOTHER FRAME HERE  -->

        <!--    SETTING MODULE STARTS HERE  -->

```








[outputImage]: images/xamarin_settings_layout_Example.png "ExampleLayout"