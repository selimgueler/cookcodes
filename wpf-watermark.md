# WPF Watermark / Placeholder for TextBox 

<p>A very simple yet powerful approach using only XAML. We will use the existing control/property TAG of the TextBox element to display a watermark / placeholder text.</p>

![alt text][outputImage]


<p>Add the following style either to a Page under <Window.Resources> node or add it to App.xaml to make it globally available to all your textboxes.</p>

```xaml

<Style x:Key="GTech:WatermarkStyle" TargetType="{x:Type TextBox}" BasedOn="{StaticResource {x:Type TextBox}}">
            <Setter Property="Template">
                <Setter.Value>
                    <ControlTemplate TargetType="{x:Type TextBox}">
                        <Grid>
                            <TextBox Text="{Binding Path=Text,
                                                RelativeSource={RelativeSource TemplatedParent}, 
                                                Mode=TwoWay,
                                                UpdateSourceTrigger=PropertyChanged}"
                                x:Name="textSource" 
                                Background="Transparent" 
                                Panel.ZIndex="2"
                                VerticalContentAlignment="Center"
                                MinHeight="24"/>
                            <TextBox Text="{TemplateBinding Tag}" Background="{TemplateBinding Background}" Panel.ZIndex="1" VerticalContentAlignment="Center" MinHeight="24">
                                <TextBox.Style>
                                    <Style TargetType="{x:Type TextBox}">
                                        <Setter Property="Foreground" Value="Transparent"/>
                                        <Style.Triggers>
                                            <DataTrigger Binding="{Binding Path=Text, Source={x:Reference textSource}}" Value="">
                                                <Setter Property="Foreground" Value="Gray"/>
                                            </DataTrigger>
                                        </Style.Triggers>
                                    </Style>
                                </TextBox.Style>
                            </TextBox>
                        </Grid>
                    </ControlTemplate>
                </Setter.Value>
            </Setter>
        </Style>
```
The color of the watermark is Gray and can be changed inside the <b>DataTrigger</b>.

Now you can use this style on any <b>TextBox</b> as follows:
```xaml

<TextBox Tag="Type here to search..." Style="{StaticResource GTech:WatermarkStyle}" Background="LightYellow" Foreground="Gray" </TextBox>

```



[outputImage]: https://github.com/selimgueler/cookcodes/blob/selimgueler-draft/OutputWPF_Watermark.gif "Output"


##### Enjoy!
