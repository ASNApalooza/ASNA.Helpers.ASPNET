# ASNA.Helpers.ASPNET

This project provides several components for making it easier to create ASP.NET applications. These components are all helper component's for Walter. However, if you are familiar with JavaScript, you could customize this code in any way you want.   

The following is a summary of what's included in this project. See below for more detail.

* **Web control helpers** This class provides miscellaneous helper classes for ASP.NET pages and controls.
* **JsonAutoComplete** An HTTP handler, and its ASHX page, that uses the ASNA.Helpers.DataServices namespace to easily provide JSON data.
* **Excel HTTP helper class.** An HTTP handler, that works with the ASNA.Helpers.DataServices Excel output adapter to redirect its Excel spreadsheets through HTTP for ASP.NET use.
* **jQuery/jQueryUI/Underscore** These are the client-side JavaScript libraries that Walter uses. 

The ComponentInstaller's `asna-helpers-aspnet` package installs this project's components into your project. After installing that package, the following files will have been written to your project. The ComponentInstaller creates all necessary target folders and it overrides any like-named files in the folders specified.

## Files installed 
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
    |   +---css
    |   |       jQueryAutoComplete.css
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

## Database naming

The ASNA.Helpers.ASPNET database components expect to find the DataGate database name indirectly referenced by the `appSettings` key `ActiveDBName` in `Web.config.` At the least your app needs to provide two `appSettings` keys: one for `ActiveDBName` and one being referenced by the `ActiveDBName` key value. This scheme lets you provide as many database names as necessary in `Web.config`, while using `ActiveDBName` to indicate which one is currently the active database name.

<pre>0001  &lt;?xml version=&quot;1.0&quot;?&gt;
0002  &lt;!--
0003    For more information on how to configure your ASP.NET application, please visit
0004    http://go.microsoft.com/fwlink/?LinkId=169433
0005    --&gt;
0006  &lt;configuration&gt;
0007    &lt;appSettings&gt;
0008      &lt;add key=&quot;ActiveDBName&quot; value=&quot;local&quot;/&gt;
0009      &lt;add key=&quot;Local&quot; value=&quot;*Public/DG NET Local&quot;/&gt;
0010      &lt;add key=&quot;Cypress&quot; value=&quot;*Public/Cypress&quot;/&gt;
0011    &lt;/appSettings&gt;
0012    &lt;system.web&gt;
0013      &lt;compilation debug=&quot;true&quot; targetFramework=&quot;4.5&quot;/&gt;
0014    &lt;/system.web&gt;
0015  &lt;/configuration&gt;
</pre>

The appSettings-driven database naming scheme above is required for the ASNA.Helpers.ASPNET database components. The code below shows how to fetch the active database name from the `appSettings` keys if you want to use the values in your own code.

<pre>DclFld ActiveDBName  Type(*String)
DclFld DBName        Type(*String) 

ActiveDBName = System.Configuration.ConfigurationManager.AppSettings["ActiveDBName"]
DBName = System.Configuration.ConfigurationManager.AppSettings[ActiveDBName]
// DBName now contains the name of the currently active DataGate database name.
</pre>



## jQueryUI AutoComplete
      
The file below shows a minimal ASPX page that uses the jQueryUI AutoComplete. 

<pre>
0001  &lt;%@ Page Language=&quot;AVR&quot; AutoEventWireup=&quot;false&quot; CodeFile=&quot;AutoComplete.aspx.vr&quot; Inherits=&quot;views_AutoComplete&quot; %&gt;
0002  
0003  &lt;!DOCTYPE html&gt;
0004  
0005  &lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot; &gt;
0006  &lt;head runat=&quot;server&quot;&gt;
0007      &lt;title&gt;Example AutoComplete&lt;/title&gt;
0008      &lt;link rel=&quot;stylesheet&quot; href=&quot;/public/vendor/jquery-ui/themes/smoothness/jquery-ui.min.css&quot;&gt;
0009      &lt;link rel=&quot;stylesheet&quot; href=&quot;/public/css/jQueryAutoComplete.css&quot;&gt;
0010  &lt;/head&gt;
0011  &lt;body&gt;
0012      &lt;form id=&quot;form1&quot; runat=&quot;server&quot;&gt;
0013      &lt;div&gt;
0014          Customer name&lt;br /&gt;
0015          &lt;asp:TextBox ID=&quot;textboxCustomerName&quot; runat=&quot;server&quot; placeholder=&quot;Customer name&quot;
0016                       EnableViewState=&quot;False&quot; ClientIDMode=&quot;Static&quot;&gt;&lt;/asp:TextBox&gt;
0017          &lt;br /&gt;
0018          Customer number &lt;br /&gt;
0019          &lt;asp:TextBox ID=&quot;textboxCustomerNumber&quot; runat=&quot;server&quot; placeholder=&quot;Customer number&quot;
0020                       EnableViewState=&quot;False&quot; ClientIDMode=&quot;Static&quot;&gt;&lt;/asp:TextBox&gt;
0021      &lt;/div&gt;
0022      &lt;/form&gt;
0023  
0024      &lt;script src=&quot;/public/vendor/jquery/dist/jquery.min.js&quot;&gt;&lt;/script&gt;
0025      &lt;script src=&quot;/public/vendor/jquery-ui/jquery-ui.min.js&quot;&gt;&lt;/script&gt;
0026      &lt;script src=&quot;/public/vendor/underscore/underscore.js&quot;&gt;&lt;/script&gt;
0027      &lt;script src=&quot;/public/js/ASNAHelpers.QueryInputArgs.js&quot;&gt;&lt;/script&gt;
0028      &lt;script src=&quot;/public/js/AutoComplete.aspx.js&quot; &gt;&lt;/script&gt;
0029  &lt;/body&gt;
0030  &lt;/html&gt;
</pre>

From the code above, the following lines need to be included in your ASPX pages to use Walter's jQueryUI AutoComplete. If you used the `ComponentInstaller` to install the `asna-helpers-aspnet` package, use exactly the paths shown; otherwise you might need to to change the paths to match your app's configuration.

#### Code annotation
* Line 8: Reference the jQueryUI CSS included with jQueryUI's AutoComplete. This example uses the Smoothness theme, but you can change it to use any of the other jQueryUI themes.    
* Line 9: Reference the jQueryAutoComplete.css file that the `asna-helpers-aspnet1 package provides. This file provides a couple of tweaks to jQueryUI's AutoComplete CSS so that a spinner is shown while fetching data.
* Line 15: This ASP.NET TextBox is where the user starts typing what is known of the customer name. After about a 300ms pause in typing, the value entered is used to look up the customer.
* Line 19: This ASP.NET TextBox is where the value produced from the lookup is placed. 
* Line 24-27: Reference the four JavaScript files provided by the `asna-helpers-aspnet` package. Be sure to include them in the order shown. 
* Line 28: This line references the small amount of JavaScript you need to provide to configure the Walter's jQueryUI AutoComplete. It's contents are shown next. 

#### The JavaScript you need to provide for each lookup
Example JavaScript needed to provide a jQueryUI AutoComplete for the ASPX page shown above. These 14 lines comprise the AutoComplete.aspx.js file referenced in line 28 of the ASPX page (as discussed in the code annotation above).

<pre>0001  $(function () {
0002      var ACCustomerName = new ASNAHelpers.QueryInputArgs();
0003      ACCustomerName.url = "../services/jsonservice.ashx";
0004      ACCustomerName.Library = "examples";
0005      ACCustomerName.File = "cmastnewl2";
0006      ACCustomerName.FieldsList = "cmname:label,cmcustno:value";
0007      ACCustomerName.Rows = 12;
0008      ACCustomerName.Query = "CMNAME >= '{CMNAME}'";
0009      ACCustomerName.addQueryParm("CMNAME");
0010      ACCustomerName.addOption("labelTargetId", "textboxCustomerName");
0011      ACCustomerName.addOption("labelValueId", "textboxCustomerNumber");
0012      ACCustomerName.addOption("showLabelOnScroll", true);
0013      ASNAHelpers.autoComplete.registerQuery(ACCustomerName);
0014  });
</pre>

The declarative JavaScript shown above is the only JavaScript you need to write to configure Walter's jQueryUI AutoComplete. See <a href="http://asnapalooza.github.io/ASNA.Helpers.DataServices.site/#qf-jquery-autocomplete">this link</a> for more details on using Walter's implementation of the jQueryUI Autocomplete. 

