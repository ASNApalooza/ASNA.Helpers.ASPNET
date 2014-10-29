# ASNA.Helpers.ASPNET

This project provides several components for making it easier to create ASP.NET applications. 

### Classes

This is a summary of what's included in this project. See below for more detail.

* **Web control helpers** This class provides miscellaneous helper classes for ASP.NET pages and controls.
* **JsonAutoComplete** An HTTP handler, and its ASHX page, that uses the ASNA.Helpers.DataServices namespace to easily provide JSON data.
* **Excel HTTP helper class.** An HTTP handler, that works with the ASNA.Helpers.DataServices Excel output adapter to redirect its Excel spreadsheets through HTTP for ASP.NET use.
* **jQuery/jQueryUI/Underscore** These are the client-side components the AutoComplete needs.

The ComponentInstaller's `asna-helpers-dataservices` package installs this project's components into your project. After installing that package, the following files will have been written to your project. The ComponentInstaller creates all necessary target folders and it overrides any like-named files in the folders specified.

The `asna-helpers-dataservices` package has a dependence on the `asna-helpers-dataservices` package. Some of the files shown below is installed with that package.    

<pre>
    \root
    |   asna-helpers-aspnet.apkg
    |   asna-helpers-dataservices.apkg
    |   projectinstaller.manifest
    |   
    +---bin
    |       ASNA.Helpers.ASPNET.dll
    |       ASNA.Helpers.ASPNET.pdb
    |       ASNA.Helpers.DataServices.dll
    |       ClosedXML.dll
    |       ClosedXML.xml
    |       DocumentFormat.OpenXml.dll
    |       log4net.dll
    |       log4net.xml
    |       Newtonsoft.Json.dll
    |       Newtonsoft.Json.xml
    |       
    +---public
    |   +---images
    |   |       concentric-spinner.gif
    |   |       icon-alert.png
    |   |       
    |   +---js
    |   |       ASNAHelpers.QueryInputArgs.js
    |   |       jQueryAutoComplete.aspx.js
    |   |       
    |   \---vendor
    |       +---jquery
    |       |   \---dist
    |       |           jquery.min.js
    |       |           jquery.min.map
    |       |           
    |       +---jquery-ui
    |       |   |   jquery-ui.min.js
    |       |   |   
    |       |   \---themes
    |       |       \---smoothness
    |       |           |   jquery-ui.min.css
    |       |           |   
    |       |           \---images
    |       |                   animated-overlay.gif
    |       |                   ui-bg_flat_0_aaaaaa_40x100.png
    |       |                   ui-bg_flat_75_ffffff_40x100.png
    |       |                   ui-bg_glass_55_fbf9ee_1x400.png
    |       |                   ui-bg_glass_65_ffffff_1x400.png
    |       |                   ui-bg_glass_75_dadada_1x400.png
    |       |                   ui-bg_glass_75_e6e6e6_1x400.png
    |       |                   ui-bg_glass_95_fef1ec_1x400.png
    |       |                   ui-bg_highlight-soft_75_cccccc_1x100.png
    |       |                   ui-icons_222222_256x240.png
    |       |                   ui-icons_2e83ff_256x240.png
    |       |                   ui-icons_454545_256x240.png
    |       |                   ui-icons_888888_256x240.png
    |       |                   ui-icons_cd0a0a_256x240.png
    |       |                   
    |       \---underscore
    |               underscore.js
    |               
    +---services
    |       JsonService.ashx
    |
</pre>

asdf
       