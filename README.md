# Apache Reverse Proxy Configuration for create-react-app

<strong>Basically, put the lines below on the Apache config file (httpd.conf)</strong>

# the /react-app here should reside at htdocs and the create-react-app should be running at http://localhost:3000/
# to access, simply go to localhost/react-app
<VirtualHost *:80>
  ProxyRequests Off
  ProxyErrorOverride Off
  ProxyPass /react-app http://localhost:3000/
  ProxyPassReverse /react-app http://localhost:3000/
</VirtualHost>

<strong>After</strong> editing the Apache config file, need to explicitly write the code for the correct bundle.js<br>on the index.html file since the original bundle.js will result in 404<br>example: `<script src="http://localhost/react-app/static/js/bundle.js"></script>`