## Adding a Custom Tab to a Web Page in OpenWrt

![opnwrt1](https://github.com/rahulelex/adding-a-custom-tab-to-a-webpage-in-openwrt/assets/46785940/ce748252-181a-4b4f-9cd2-341fa8a74862)

To add a custom tab to a web page in OpenWrt, which is hosted at http://192.168.1.1/cgi-bin/luci/
### Step 1: Creating the .lua file:
Make sure the ***nano*** command is installed in your OpenWrt, if not install it using the command 'opkg update' and then 'opkg install nano'. 
```sh
nano /usr/lib/lua/luci/controller/my_page.lua
```

### Step 2: Writing code in my_page.lua
```ruby
module("luci.controller.my_page", package.seeall)
function index()
    entry({"admin", "my_page"}, template("my_page"), "My Webpage", 70)
end
```
- ***"admin", "my_page"***: This defines the URL path where the tab will appear. In this case, it will appear under the "admin" section with the label "my_page".
- ***template("my_page")***: Refers to the template file to be used for rendering the content of the tab. The template file is named ***my_page.htm*** in your instructions.
- ***"My Webpage"***: This is the label that will be displayed for the tab in the navigation menu.
- ***70***: This is the priority of the tab. It determines the order in which the tabs appear in the menu. Lower numbers will appear first.

### Step 3: Generating the .htm file
```sh
nano /usr/lib/lua/luci/view/my_webpage.htm
```
### Step 4: Writing content in my_webpage.htm
```ruby
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<!-- <meta http-equiv="refresh" content="0; URL=http://localhost:8090/my-page"> -->
<title>Redirect to Your Domain</title>
</head>
<%#
Copyright 2008 Steven Barth <steven@midlink.org>
Copyright 2008-2019 Jo-Philipp Wich <jo@mein.io>
Licensed to the public under the Apache License 2.0.
-%>

<script type="text/javascript">
var host = document.location.hostname;
var redirectUrl = `http://${host}:8080/`;
document.location.replace(redirectUrl);
</script>

<body>
<h1>Redirecting to Your Domain...</h1>
</body>
</html>
```
By just following above mentioned 4 steps you will be able to add a custom tab in the existing web page of openwrt hosted at http://192.168.1.1/cgi-bin/luci/

## License
**Free Software, Hell Yeah!**

## Authors
- [Rahul Gupta](https://github.com/rahulelex)
