Los no seguros
```bash
sudo vim /etc/apache2/sites-enabled/000-defualt.conf
```

```conf
<VirtualHost aulavirutal.randion.es:80>
	ServerName aulavirutal.randion.es
	Redirect
</VirtualHost>

<VirtualHost ficticio1.randion.es:80>
	ServerName fct.randion.es
	DocumentRoot /var/www/ficticio
</VirtualHost>

<VirtualHost fct.randion.es:80>
	ServerName fct.randion.es
	DocumentRoot /var/www/fct/public
	.
	.
	.
</VirtualHost>
```

Los seguros

```bash
sudo vim /etc/apache2/sites-enabled/000-defualt-le-ssl.conf
```

```conf
<VirtualHost aulavirutal.randion.es:443>
	ServerName aulavirutal.randion.es
	DocumentRoot /var/www/moodle
	RewriteEngine on
	.
	.
	.
</VirtualHost>
```

### Puertos
80 http?
443 https?

```bash
vim ifc33b.conf
```

```conf
<VirtualHost mgomez.randion.es:443>
	ServerName mgomez.randion.es
	DocumentRoot /var/www/mi_carpeta
</VirtualHost>
```