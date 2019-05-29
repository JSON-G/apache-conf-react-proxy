# Apache Reverse Proxy Configuration for create-react-app

<strong>Basically, put the lines below on the Apache config file (httpd.conf)</strong>

&lt;VirtualHost *:80&gt;<br>
&nbsp;&nbsp;ProxyRequests Off<br>
&nbsp;&nbsp;ProxyErrorOverride Off<br>
&nbsp;&nbsp;ProxyPass /react-app http://localhost:3000/<br>
&nbsp;&nbsp;ProxyPassReverse /react-app http://localhost:3000/<br>
&lt;/VirtualHost&gt;<br>


<ul>
<li>the /react-app should reside at htdocs and the create-react-app should be running at http://localhost:3000/</li>
<li>to access, simply go to localhost/react-app</li>
</ul><br>

<strong>After</strong> editing the Apache config file, need to explicitly write the code for the correct bundle.js<br>on the index.html file since the original bundle.js will result in 404<br>example: `<script src="http://localhost/react-app/static/js/bundle.js"></script>` (recommended to be placed after body tags)
