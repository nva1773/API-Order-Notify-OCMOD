ABOUT
The modifier adds the ability to make "GET" requests through the API to receive new, unprocessed orders.
I.e. orders that have the Status "Pending" or "Processing".
It is also possible to enter the IP address of users who are allowed access to the API in the form of a mask using "*".

INSTALLATION
Through the opercard add-on installer:
 - go to the "Extensions/Installer" section and click the "Upload" button;
 - select the downloaded file and wait for the text “Add installed successfully” to appear.
After installation, clear the modifier cache:
 - go to the "Extensions/Modifications" and click the "Clear" and "Refresh" buttons.
 
INFORMATION
Localization: English, Russian, Ukrainian,
Support is provided by the latest languages: English, Russian, Ukrainian,
OpenCart 3.0 / ocStore 3.0
Activation method: Without activation
Ioncube Loader: -
Zvernennya to the server of the retailer: -
The retailer server is unavailable: The extension is working
Lots of templates: *

SETTINGS
After installing the modifier, you can add an API user if needed.
To do this, select "System > Users > API" in the admin panel and click the "Add" button.
In the form that appears, enter the Name and Key (or generate it) and change the Status to "Enabled",
and in the IP addresses tab, add an address or a list of addresses that will be allowed access to the API.
You can add the address as a mask using "* (eg 192.168.*.*).

TESTING
You can now start making requests through the API.
1. We receive an API-Token using the Name and Key:
https://you.site.url/index.php?route=api/login&api_username=API-USER&api_key=API-KEY
or, if the Default Name is used, then only the Key of this user:
https://you.site.url/index.php?route=api/login&api_key=API-KEY
If the request was successful, you will receive the following response:
{"success":"true","api_token":"a4cf14c8c106cb0ab95c96b2ce","error":""}
copy the API-Token, it will be needed to access the order information.
If not, there are two possible answers:
{"success":"false","api_token":"","error":"Incorrect API username or key!"}
or
{"success":"false","api_token":"","error":"Your IP 192.169.12.1 does not have access to the API!"}
2. Using the API-Token, we make a request to receive unprocessed orders:
https://you.site.url/index.php?route=api/sale/orders&api_token=a4cf14c8c106cb0ab95c96b2ce
we get an answer, for example:
{"success":"true","orders":[{"order_id":"1","customer":"Test Test","date_added":"09\/06\/2024 11:41:54" ,"total":"500.00 \u0433\u0440\u043d."}],"orders_total":1,"sale_total":500,"error":""}
3. Now knowing the number of the new order, we request its full information:
https://you.site.url/index.php?route=api/sale/order&api_token=a4cf14c8c106cb0ab95c96b2ce&order_id=1
answer:
{"success":"true","order_info":";-\n\u2116 \u0437\u0430\u043c\u043e\u0432\u043b\u0435\u043d\u043d\u044f: 1\n\u0414\u0430\u0442\u0430 \u0437\u0430\u043c\u043e\u0432\u043b\u0435\u043d\u043d\u044f: 09\/06\/2024 11:41:54\n\u0406\u043c\u044f: \u0428\u0432\u0438\u0434\u043a\u0438\u0439 \u0437\u0430\u043a\u0430\u0437\n\u0422\u0435\u043b\u0435\u0444\u043e\u043d: 0987654321\n;-\nMacBook\n\u041a\u043e\u0434 \u0442\u043e\u0432\u0430\u0440\u0443: Product 16       \u041a\u0456\u043b\u044c\u043a\u0456\u0441\u0442\u044c: 1\n\n\u0420\u0430\u0437\u043e\u043c: 500.00 \u0433\u0440\u043d.\n;-\n\u0411\u0430\u043d\u043a\u0456\u0432\u0441\u044c\u043a\u0456\u0439 \u043f\u0435\u0440\u0435\u043a\u0430\u0437\n\n;-\n","error":""}

For the convenience of testing, to avoid manual work, there is an "index.html" file in the testing-api.zip archive,
with the help of which everything described above is done simply and clearl. Simply unzip the archive and run index.html in any Internet browser.