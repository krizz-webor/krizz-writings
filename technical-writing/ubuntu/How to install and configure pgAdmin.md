## How to install and configure pgAdmin
pgAdmin is an open-source administration and development platform for PostgreSQL and its related database management systems. Written in Python and jQuery, it supports all the features found in PostgreSQL. You can use pgAdmin to do everything from writing basic SQL queries to monitoring your databases and configuring advanced database architectures.

## Step 1 — Installing pgAdmin and its Dependencies

As of this writing, the most recent version of pgAdmin is pgAdmin 4, while the most recent version available through the official Ubuntu repositories is pgAdmin 3. pgAdmin 3 is no longer supported though, and the project maintainers recommend installing pgAdmin 4. In this step, we will go over the process of installing the latest version of pgAdmin 4 within a virtual environment and installing its dependencies using `apt`.

To begin, update your server’s package index if you haven’t done so recently:

`sudo apt update`

Next, install the following dependencies. These include` libgmp3-dev`, a multiprecision arithmetic library; `libpq-dev`, which includes header files and a static library that helps communication with a PostgreSQL backend; and `libapache2-mod-wsgi-py3`, an Apache module that allows you to host Python-based web applications within Apache:

`sudo apt install libgmp3-dev libpq-dev libapache2-mod-wsgi-py3`

Following this, create a few directories where pgAdmin will store its sessions data, storage data, and logs:

    sudo mkdir -p /var/lib/pgadmin4/sessions
    sudo mkdir /var/lib/pgadmin4/storage
    sudo mkdir /var/log/pgadmin4

Then, change ownership of these directories to your non-root user and group. This is necessary because they are currently owned by your **root** user, but we will install pgAdmin from a virtual environment owned by your non-root user, and the installation process involves creating some files within these directories. After the installation, however, we will change the ownership over to the **www-data** user and group so it can be served to the web:

    sudo chown -R sammy:sammy /var/lib/pgadmin4
    sudo chown -R sammy:sammy /var/log/pgadmin4

Next, open up your virtual environment. Navigate to the directory your programming environment is in and activate it.
we’ll go to the `environments` directory and activate the `my_env` environment:

    cd environments/
    source my_env/bin/activate

After activating the virtual environment, it would be prudent to ensure that you have the latest version of` pip `installed on your system. The version of `pip` that’s available from the default Ubuntu 18.04 repositories is version `9.0.1`, while the latest version is `21.0.1`. If installed the `pyton3-pip` package as outlined in the prerequisite Python installation tutorial but you haven’t upgraded it to the latest version, you will run into problems when configuring pgAdmin in the next step.

To upgrade `pip` to the latest version, run the following command:

`python -m pip install -U pip`

Following this, download the pgAdmin 4 source code onto your machine. To find the latest version of the source code, navigate to the [pgAdmin 4 (Python Wheel) Download page](https://www.postgresql.org/ftp/pgadmin/pgadmin4/). Click the link for the latest version ( `v5.1`, as of this writing), then on the next page click the link reading **pip**. From this **File Browser** page, copy the file link that ends with` .whl` — the standard built-package format used for Python distributions. Then go back to your terminal and run the following `wget` command, making sure to replace the link with the one you copied from the PostgreSQL site, which will download the `.whl` file to your server:

`wget https://ftp.postgresql.org/pub/pgadmin/pgadmin4/v5.1/pip/pgadmin4-5.1-py3-none-any.whl`

Next install the `wheel` package, the reference implementation of the wheel packaging standard. A Python library, this package serves as an extension for building wheels and includes a command line tool for working with `.whl` files:

`python -m pip install wheel`

Then install pgAdmin 4 package with the following command:

`python -m pip install pgadmin4-5.1-py3-none-any.whl`

That takes care of installing pgAdmin and its dependencies. Before connecting it to your database, though, there are a few changes you’ll need to make to the program’s configuration.

## Step 2 — Configuring pgAdmin 4

Although pgAdmin has been installed on your server, there are still a few steps you must go through to ensure it has the permissions and configurations needed to allow it to correctly serve the web interface.

pgAdmin’s main configuration file, `config.py`, is read before any other configuration file. Its contents can be used as a reference point for further configuration settings that can be specified in pgAdmin’s other config files, but to avoid unforeseen errors, you should not edit the` config.py` file itself. We will add some configuration changes to a new file, named `config_local.py`, which will be read after the primary one.

Create this file now using your preferred text editor. Here, we will use nano:

`nano my_env/lib/python3.6/site-packages/pgadmin4/config_local.py`

In your editor, add the following content:

`environments/my_env/lib/python3.6/site-packages/pgadmin4/config_local.py`

    LOG_FILE = '/var/log/pgadmin4/pgadmin4.log'
    SQLITE_PATH = '/var/lib/pgadmin4/pgadmin4.db'
    SESSION_DB_PATH = '/var/lib/pgadmin4/sessions'
    STORAGE_DIR = '/var/lib/pgadmin4/storage'
    SERVER_MODE = True

Here are what these five directives do:

* `LOG_FILE`: this defines the file in which pgAdmin’s logs will be stored.
 * `SQLITE_PATH`: pgAdmin stores user-related data in an SQLite database, and this directive points the pgAdmin software to this configuration database. Because this file is located under the persistent directory `/var/lib/pgadmin4/`, your user data will not be lost after you upgrade.
* `SESSION_DB_PATH`: specifies which directory will be used to store session data.
* `STORAGE_DIR`: defines where pgAdmin will store other data, like backups and security certificates.
* `SERVER_MODE`: setting this directive to `True` tells pgAdmin to run in Server mode, as opposed to Desktop mode.

Notice that each of these file paths point to the directories you created in Step 1.

After adding these lines, save and close the file. If you used `nano`, do so by press `CTRL + X` followed by `Y` and then `ENTER`.

With those configurations in place, run the pgAdmin setup script to set your login credentials:

`python my_env/lib/python3.6/site-packages/pgadmin4/setup.py`

After running this command, you will see a prompt asking for your email address and a password. These will serve as your login credentials when you access pgAdmin later on, so be sure to remember or take note of what you enter here:

    Output
    . . .
    Enter the email address and password to use for the initial pgAdmin user account:
    
    Email address: sammy@example.com
    Password:
    Retype password:

Following this, deactivate your virtual environment:

`deactivate`

Recall the file paths you specified in the `config_local.py` file. These files are held within the directories you created in Step 1, which are currently owned by your non-root user. They must, however, be accessible by the user and group running your web server. By default on Ubuntu 18.04, these are the **www-data** user and group, so update the permissions on the following directories to give **www-data** ownership over both of them:

    sudo chown -R www-data:www-data /var/lib/pgadmin4/
    sudo chown -R www-data:www-data /var/log/pgadmin4/

With that, pgAdmin is fully configured. However, the program isn’t yet being served from your server, so it remains inaccessible. To resolve this, we will configure Apache to serve pgAdmin so you can access its user interface through a web browser.

## Step 3 — Configuring Apache

  The Apache web server uses *virtual* hosts to encapsulate configuration details and host more than one domain from a single server. If you followed the prerequisite Apache tutorial, you may have set up an example virtual host file under the name `your_domain.conf`, but in this step we will create a new one from which we can serve the pgAdmin web interface.

To begin, make sure you’re in your root directory:

`cd /`

Then create a new file in your `/sites-available/` directory called `pgadmin4.conf`. This will be your server’s virtual host file:

`sudo nano /etc/apache2/sites-available/pgadmin4.conf`

Add the following content to this file, being sure to update the highlighted parts to align with your own configuration:


`/etc/apache2/sites-available/pgadmin4.conf`

    <VirtualHost *>
        ServerName your_server_ip
     WSGIDaemonProcess pgadmin processes=1 threads=25 python-home=/home/sammy/environments/my_env
        WSGIScriptAlias / /home/sammy/environments/my_env/lib/python3.6/site-packages/pgadmin4/pgAdmin4.wsgi
        
        <Directory "/home/sammy/environments/my_env/lib/python3.6/site-packages/pgadmin4/">
            WSGIProcessGroup pgadmin
            WSGIApplicationGroup %{GLOBAL}
            Require all granted
        </Directory>
    </VirtualHost>

Save and close the virtual host file. Next, use the `a2dissite` script to disable the default virtual host file, `000-default.conf`:

`sudo a2dissite 000-default.conf`

Note: If you followed the prerequisite Apache tutorial, you may have already disabled `000-default.conf` and set up an example virtual host configuration file (named `your_domain.conf` in the prerequisite). If this is the case, you will need to disable the `your_domain.conf` virtual host file with the following command:

`sudo a2dissite your_domain.conf`

Then use the `a2ensite `script to enable your `pgadmin4.conf` virtual host file. This will create a symbolic link from the virtual host file in the `/sites-available/` directory to the `/sites-enabled/` directory:

`sudo a2ensite pgadmin4.conf`

Following this, test that your configuration file’s syntax is correct:

`apachectl configtest`

If your configuration file is all in order, you will see `Syntax OK`. If you see an error in the output, reopen the `pgadmin4.conf` file and double check that your IP address and file paths are all correct, then rerun the `configtest`.

Once you see `Syntax OK` in your output, restart the Apache service so it reads your new virtual host file:

`sudo systemctl restart apache2`

pgAdmin is now fully installed and configured. Next, we’ll go over how to access pgAdmin from a browser before connecting it to your PostgreSQL database.

## Step 4 — Accessing pgAdmin

On your local machine, open up your preferred web browser and navigate to your server’s IP address:

`http://your_server_ip`

Once there, you’ll be presented with a login screen similar to the following:

https://assets.digitalocean.com/articles/pgadmin/pgadmin_login_blank.png

Enter the login credentials you defined in Step 2, and you’ll be taken to the pgAdmin Welcome Screen:

https://assets.digitalocean.com/articles/pgadmin/pgadmin_welcome_page_1.png

Now that you’ve confirmed you can access the pgAdmin interface, all that’s left to do is to connect pgAdmin to your PostgreSQL database. Before doing so, though, you’ll need to make one minor change to your PostgreSQL superuser’s configuration.
## Step 5 — Configuring your PostgreSQL User
By default in PostgreSQL, you authenticate as database users using the “Identification Protocol,” or “ident,” authentication method. This involves PostgreSQL taking the client’s Ubuntu username and using it as the allowed database username. This can allow for greater security in many cases, but it can also cause issues in instances where you’d like an outside program, such as pgAdmin, to connect to one of your databases. To resolve this, we will set a password for this PostgreSQL role which will allow pgAdmin to connect to your database.

From your terminal, open the PostgreSQL prompt under your superuser role: