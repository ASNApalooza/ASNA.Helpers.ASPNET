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
       

<pre>
0001  &lt;%@ Page Language=&quot;AVR&quot; AutoEventWireup=&quot;false&quot; CodeFile=&quot;AutoComplete.aspx.vr&quot; Inherits=&quot;views_AutoComplete&quot; %&gt;
0002  
0003  &lt;!DOCTYPE html&quot;&gt;
0004  &lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot; &gt;
0005  &lt;head runat=&quot;server&quot;&gt;
0006      &lt;title&gt;Example AutoComplete&lt;/title&gt;
0007  
0008     &lt;link rel=&quot;stylesheet&quot; href=&quot;/public/vendor/jquery-ui/themes/smoothness/jquery-ui.min.css&quot;&gt;
0009  
0010     &lt;style&gt;
0011     .ui-autocomplete-loading {
0012      background-image: url(&#39;/public/images/concentric-spinner.gif&#39;);
0013      background-position: 98% 50%;
0014      background-repeat: no-repeat;
0015  }
0016  
0017      .my-ui-icon-alert {
0018          background: white url(&#39;../images/icon-alert.png&#39;) right center no-repeat;
0019      }
0020  &lt;/style&gt;
0021  
0022  &lt;/head&gt;
0023  &lt;body&gt;
0024      &lt;form id=&quot;form1&quot; runat=&quot;server&quot;&gt;
0025          &lt;div&gt;
0026              Customer name&lt;br /&gt;
0027              &lt;asp:TextBox ID=&quot;textboxCustomerName&quot; runat=&quot;server&quot; placeholder=&quot;Customer name&quot;
0028                           EnableViewState=&quot;False&quot; ClientIDMode=&quot;Static&quot;&gt;&lt;/asp:TextBox&gt;
0029              &lt;br /&gt;
0030              Customer number &lt;br /&gt;
0031              &lt;asp:TextBox ID=&quot;textboxCustomerNumber&quot; runat=&quot;server&quot; placeholder=&quot;Customer number&quot;
0032                           EnableViewState=&quot;False&quot; ClientIDMode=&quot;Static&quot;&gt;&lt;/asp:TextBox&gt;
0033          &lt;/div&gt;
0034      &lt;/form&gt;
0035  
0036      &lt;script src=&quot;/public/vendor/jquery/dist/jquery.min.js&quot;&gt;&lt;/script&gt;
0037      &lt;script src=&quot;/public/vendor/jquery-ui/jquery-ui.min.js&quot;&gt;&lt;/script&gt;
0038      &lt;script src=&quot;/public/vendor/underscore/underscore.js&quot;&gt;&lt;/script&gt;
0039      &lt;script src=&quot;/public/js/ASNAHelpers.QueryInputArgs.js&quot;&gt;&lt;/script&gt;
0040      &lt;script src=&quot;/public/js/AutoComplete.aspx.js&quot; &gt;&lt;/script&gt;
0041  &lt;/body&gt;
0042  &lt;/html&gt;
</pre>