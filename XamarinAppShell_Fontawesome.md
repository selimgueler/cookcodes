# Using Fontawesome Font in Xamarin Applications

## Get the OTF file from Fontawesome 

### Step 1 - Download 
Download the files from Fontawesome website. As of writing this entry (Fontawesome version 5 Free), they provide 3 different otf files in a zip file.
Check their website to find out which one the files you need. This instruction will use only one single otf file, however if you need multiple otf files it is very simple to figure it out.

(Optional) Remove the spaces in the filename. It may cause problems on different platforms. For instance to "FontAwesome5Free-Solid-900.otf".

### Step 2 - Add in Xamarin Project (Shared Project) 

Create a folder in your shared xamarin project and paste your otf font file here. (optional) 

### Step 3 - Set "Build Action" of the font file

If you forget this step, the icons font be displayed at all. 
Choose the font file from Solution Explorer to display its Properties.

Go to AssemblyInfo.cs and register the font in the assembly.

```cs
[assembly: ExportFont("FontAwesome5Free-Solid-900.otf", Alias = "Fontawesome")]
```

The "Alias" is important. We will use the alias in our xamarin view pages as our resource. 


## Using Fontawesome Icon in a Simple XAML Page

A very simple example on how to use the exported font as icon. 
The only tricky step is to convert the Glyph i.e. the font code that you get from the fontawesome website. 

For example for the code **f080** which is displayed on the website, you need to convert this value to 
```&#xf080;``` . Do NOT forget the semicolon!  


```xml
<Image>
            <Image.Source>
                <FontImageSource Glyph="&#xf080;"
                                 FontFamily="Fontawesome"
                                 Size="44">
                    
                </FontImageSource>
            </Image.Source>
 </Image>
 ```
 
 
## Using Fontawesome Icon in the AppShell in Tab Bar

```xml
<TabBar>
  <!-- Remove this, here for reference only <ShellContent Title="Home" Route="home" Icon="HomePath.png" ContentTemplate="{DataTemplate local:MainPage}" /> -->
  <Tab Title="Home" Route="home" >
            <Tab.Icon>
                <FontImageSource FontFamily="Fontawesome" Glyph="&#xe065;" />
            </Tab.Icon>
            <ShellContent ContentTemplate="{DataTemplate local:MainPage}"></ShellContent>
        </Tab>
  
 </TabBar>
 ```
 
 
 [outputImage]: images/image.png "AppShell in Android with Font Icons"
