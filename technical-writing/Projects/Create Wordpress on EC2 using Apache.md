## Deploy Wordpress website on AWS using Apache2

As WordPress requires a MySQL database to store its data, create an RDS

Go to the Amazon RDS console. Click "Create database".

![pGcrI0R6-7sKrSyYNB4hXP7GpkI50wCoY4p66xc-4SIhK3xJpekcT7pGSF4MmwRm7uN2r-X4xwrID2On7s4U8oe3igHfse8UY59L_tQ](../../media/pGcrI0R6-7sKrSyYNB4hXP7GpkI50wCoY4p66xc-4SIhK3xJpekcT7pGSF4MmwRm7uN2r-X4xwrID2On7s4U8oe3igHfse8UY59L_tQ.png)

Select "MySQL" as the engine type.

![5ztuGzzo7awc8keJ-TbZLx9KI2K3ZukM6WtU1GhnpTEWjXivO4skXiaHpzpECf900163fGeC36Pyz_x2_q_WqBrv2CEDbrNGWfQYkGb7](../../media/5ztuGzzo7awc8keJ-TbZLx9KI2K3ZukM6WtU1GhnpTEWjXivO4skXiaHpzpECf900163fGeC36Pyz_x2_q_WqBrv2CEDbrNGWfQYkGb7.png)

Choose the "Free tier" template for "DB instance class".

![F5OnJVBquiA018DX_fu7NV7OWH6TcRLHYsqq5KjvbCwmiL126Pp3oto7C8equDlImUocHQ0tN22qbvR01ZbRGrTwkQC8yyA89g1y7zvi_A](../../media/F5OnJVBquiA018DX_fu7NV7OWH6TcRLHYsqq5KjvbCwmiL126Pp3oto7C8equDlImUocHQ0tN22qbvR01ZbRGrTwkQC8yyA89g1y7zvi_A.png)

Enter a unique name for the "DB instance identifier".

Set the "Master username" and "Master password" for the database.

![P7Gs9lz1bUDYHVB5IRvxRZ7UDkt9nsaX42tPTtg_1VgjnZ6BXxdGQ7l_jFLd1-29yQtUdJpPh_68Urz_Lm6oJzQqWZbI09DVDAGYh_yMwg](../../media/P7Gs9lz1bUDYHVB5IRvxRZ7UDkt9nsaX42tPTtg_1VgjnZ6BXxdGQ7l_jFLd1-29yQtUdJpPh_68Urz_Lm6oJzQqWZbI09DVDAGYh_yMwg.png)

Set the "Virtual Private Cloud (VPC)" and "Subnet group" to create the instance in. Leave the other settings at their default values.

![e1qdvQ7IhPNUqEcxecXnXevEg3iyf3qMMcZD0sHyUT6SewSe-J3-5G7_pH0ml6pPoXWsMQEzCSCZx8QsFZoBxf4qSNDplNXKYD-ggqBm](../../media/e1qdvQ7IhPNUqEcxecXnXevEg3iyf3qMMcZD0sHyUT6SewSe-J3-5G7_pH0ml6pPoXWsMQEzCSCZx8QsFZoBxf4qSNDplNXKYD-ggqBm.png)

![O9e0xqZP8J_IKguPFy7xPQ6EQOmPBhsanNb13oDgL11Brl661b3D0ZuhhPkl2Od6SVa6N3HI7Z58OtEJ5EZNlexP900DhrvVS8c9hV0](../../media/O9e0xqZP8J_IKguPFy7xPQ6EQOmPBhsanNb13oDgL11Brl661b3D0ZuhhPkl2Od6SVa6N3HI7Z58OtEJ5EZNlexP900DhrvVS8c9hV0.png)

Choose 'Default VPC'

![BsJmLEWErLXkZ721M_t86SvuW0fv1YwXSRdlcT5ELXgKdgtEcgXOu7IhGHaPiyCmvJcKDtRvkagactilk3QH5WvMwgHF0OF-zng1Clmnfw](../../media/BsJmLEWErLXkZ721M_t86SvuW0fv1YwXSRdlcT5ELXgKdgtEcgXOu7IhGHaPiyCmvJcKDtRvkagactilk3QH5WvMwgHF0OF-zng1Clmnfw.png)

![MRe37xpklBkFJ7NgVgEKCL7XDbvY9_ytE4KEqeZ3TEOER2gl9o0_sNx9zdB6ebQ7RwMEmx59xkIfaNoBSx2frWwTGQULrltShVFtbdtx](../../media/MRe37xpklBkFJ7NgVgEKCL7XDbvY9_ytE4KEqeZ3TEOER2gl9o0_sNx9zdB6ebQ7RwMEmx59xkIfaNoBSx2frWwTGQULrltShVFtbdtx.png)

Click on "create database"

![5iw5mdJ8GT3S40pnimkhPyfxjPVYMnVlreQ5I2agbksd1bnQm5Y3msykhAg4KOQ3i0pEcOVM-aOKdDkSvXCBuy7k71Z4wCsp7Bm6UTgr](../../media/5iw5mdJ8GT3S40pnimkhPyfxjPVYMnVlreQ5I2agbksd1bnQm5Y3msykhAg4KOQ3i0pEcOVM-aOKdDkSvXCBuy7k71Z4wCsp7Bm6UTgr.png)

Database is created.

![k4ZAm5ATO-6F_KTf8jjH4jAEydMVON6k25D2_B_l74lkryPvOJuMOCTdfLLDbrtGyC6v_yK5D_oy4gXCjaS_4F9Mc7fX9QWyii8nmeGR-g](../../media/k4ZAm5ATO-6F_KTf8jjH4jAEydMVON6k25D2_B_l74lkryPvOJuMOCTdfLLDbrtGyC6v_yK5D_oy4gXCjaS_4F9Mc7fX9QWyii8nmeGR-g.png)

#### To configure this WordPress site, you will create the following resources in AWS:
An Amazon EC2 instance to install and host the WordPress application.

Go to the Amazon EC2 console., Click "Launch Instance", Choose a Linux AMI.

Choose an instance type, such as t2.micro, Choose a VPC and subnet.

Configure security group rules to allow inbound traffic on the appropriate port for the type of database you are using (e.g. port 3306 for MySQL).

![xYpdxVPop6ywme2MAFxuYtrezzEUoPqcZAa1Xr1EmL_kKN6EJ7_6B1R4aUPxi7Xo2hfhS-Qfocx_8niq0PXfbS-fSuENNf0JbvVdDj7P](../../media/xYpdxVPop6ywme2MAFxuYtrezzEUoPqcZAa1Xr1EmL_kKN6EJ7_6B1R4aUPxi7Xo2hfhS-Qfocx_8niq0PXfbS-fSuENNf0JbvVdDj7P.png)

#### An Amazon RDS for MySQL database to store your WordPress data.
Choose the MySQL database you created, go to the Connectivity & security tab in the display and choose the security group listed in VPC security groups. The console will take you to the security group configured for your database.

![URHiOp5wEc1U7EpS47gWQC3XCAgReS7M3EnPOaMF2xk4CpgLSTZOmuWB_XBjV8217-24Ncrbwq5i81xxo_zr0Vapzx9-HbJfNQTS-PP3vw](../../media/URHiOp5wEc1U7EpS47gWQC3XCAgReS7M3EnPOaMF2xk4CpgLSTZOmuWB_XBjV8217-24Ncrbwq5i81xxo_zr0Vapzx9-HbJfNQTS-PP3vw.png)

Select the Inbound rules tab, then choose the Edit inbound rules button to change the rules for your security group.

![BtrXt3KNGrMg7h_LpKv8bR85Ti6I_gAQl5WJq5GX_e-g4gsknXmAVdsysorFL3diHzKv9aToHAFplUb9eG1Jd_suGwDTuFyrZHldZ95v4g](../../media/BtrXt3KNGrMg7h_LpKv8bR85Ti6I_gAQl5WJq5GX_e-g4gsknXmAVdsysorFL3diHzKv9aToHAFplUb9eG1Jd_suGwDTuFyrZHldZ95v4g.png)

![cpDFdM5H0GqpKDsk1GPw15lihsXB1GGho6Y2yccogNIAjp5x2huMF0YUzjyD1qy2HvPuXVMzVge5GmaU2tg5R4KzdhsQHeTDhDeTQsI](../../media/cpDFdM5H0GqpKDsk1GPw15lihsXB1GGho6Y2yccogNIAjp5x2huMF0YUzjyD1qy2HvPuXVMzVge5GmaU2tg5R4KzdhsQHeTDhDeTQsI.png)

Change the Type property to MYSQL/Aurora, which will update the Protocol and Port range to the proper values.

Choose the security group that you used for your EC2 instance.

![DQQZ8AYVeNMLMo-AibDNjeFc21UyYIO6iKZ83YFaerlVt0so1VhwE1xS31FyLLloUgvUwfBah1CXarOTID0rrfbew4XYPM01Wyf5cyCG](../../media/DQQZ8AYVeNMLMo-AibDNjeFc21UyYIO6iKZ83YFaerlVt0so1VhwE1xS31FyLLloUgvUwfBah1CXarOTID0rrfbew4XYPM01Wyf5cyCG.png)

SSH into your EC2 instance

![0rEWxY4x5GuK1tCXnxWjdrCNL4KrD1Gxs-YTWmZJqPzhoxpiy072BoxW3rTGKMPbWOQVsV5C8ow8a3ys_AYcqvl0ODEdMgAxRLy2I80](../../media/0rEWxY4x5GuK1tCXnxWjdrCNL4KrD1Gxs-YTWmZJqPzhoxpiy072BoxW3rTGKMPbWOQVsV5C8ow8a3ys_AYcqvl0ODEdMgAxRLy2I80.png)

run the following command in your terminal to install a MySQL client to interact with the database.

    sudo apt install mysql-client-core-8.8

![dQxIGo4JkbTcE-XXo3twGa_ScFSRhb0J-BiAF5vPx5c6CbPJ7jzlPokBOeUttr3dU4rZg9pOK76xsqTJWAFWBx-ioTnGHBnCt_nUObEi](../../media/dQxIGo4JkbTcE-XXo3twGa_ScFSRhb0J-BiAF5vPx5c6CbPJ7jzlPokBOeUttr3dU4rZg9pOK76xsqTJWAFWBx-ioTnGHBnCt_nUObEi.png)

Run the following command in your terminal to connect to your MySQL database. Replace “<user>” and “<password>” with the master username and password you configured when creating your Amazon RDS database. -h is host which is RDS database endpoint.

    mysql -h <rds-database-endpoint> -P <port-no> -u <user> -p <password>

Finally, create a database user for your WordPress application and give the user permission to access the wordpress database.

Run the following commands in your terminal:

    CREATE DATABASE wordpress;
    CREATE USER 'wordpress' IDENTIFIED BY 'wordpress-pass';
    GRANT ALL PRIVILEGES ON wordpress.* TO wordpress;
    FLUSH PRIVILEGES;
    Exit

you should use a better password than wordpress-pass to secure your database.

![t9ivXpdFpq-J-bM4dOGDd5zBcOlH3NOAeqdWWEV-_B7CXSgmGUHqgmTnryYC1tVb3Pmv5upaMJL5bo5Di1DRbVo5gVngNPLgw5Lj0RqKIg](../../media/t9ivXpdFpq-J-bM4dOGDd5zBcOlH3NOAeqdWWEV-_B7CXSgmGUHqgmTnryYC1tVb3Pmv5upaMJL5bo5Di1DRbVo5gVngNPLgw5Lj0RqKIg.png)

To run WordPress, you need to run a web server on your EC2 instance.

To install Apache on your EC2 instance, run the following command in your terminal:

    sudo apt-get install apache2

![HGhN38Zq_IxdmnG9f8ZuRqk6oWr_FRUGxOU5otC81qk6ZpiNP_chONFikjyn774IleXcng540XzCtykIJ-mNwOw9XkGMfhJrIB-cLf6o](../../media/HGhN38Zq_IxdmnG9f8ZuRqk6oWr_FRUGxOU5otC81qk6ZpiNP_chONFikjyn774IleXcng540XzCtykIJ-mNwOw9XkGMfhJrIB-cLf6o.png)

To start the Apache web server, run the following command in your terminal:

    systemctl restart apache2

You can see that your Apache web server is working by browsing public-ip of your ec2 instance.

![5eZ4UaPSoIZMe25jgfxLZivCyRu76JyJ5adTXxqz6DMhsV7-L7Lm8GFsQDrGfQUpnKLTtJUz6f95J4rBf5nv_GBpqwT2CrQtLvCjHT_ufQ](../../media/5eZ4UaPSoIZMe25jgfxLZivCyRu76JyJ5adTXxqz6DMhsV7-L7Lm8GFsQDrGfQUpnKLTtJUz6f95J4rBf5nv_GBpqwT2CrQtLvCjHT_ufQ.png)

#### Setup the server and post your new Wordpress app.
First, download and uncompressed the software by running the following commands in your terminal:

    wget https://wordpress.org/latest.tar.g
    tar -xzf latest.tar.gz

![oRtCgievNwpJ_40zWEgxCJzceA_HfsB05wKpjkkCCmzvGf3McdXb48iz-cKTcbuP9_aFoTDYr6XYlo86cic76dgK1jog-uUmCWFMnVV0](../../media/oRtCgievNwpJ_40zWEgxCJzceA_HfsB05wKpjkkCCmzvGf3McdXb48iz-cKTcbuP9_aFoTDYr6XYlo86cic76dgK1jog-uUmCWFMnVV0.png)

you will see a tar file and a directory called wordpress with the uncompressed contents using ls command.

![pEBNspUtBYM6gBSvmsfyImO9JAfkDX23KWVExrF6CmLn2bEex4oHDO-bgu9Id0L5KnF6YDds0AmlidORLbH6nJNjhHF9NVwysyn-mIx-](../../media/pEBNspUtBYM6gBSvmsfyImO9JAfkDX23KWVExrF6CmLn2bEex4oHDO-bgu9Id0L5KnF6YDds0AmlidORLbH6nJNjhHF9NVwysyn-mIx-.png)

Change the directory to the wordpress directory and create a copy of the default config file using the following commands

    open the wp-config.php file

![v_lG-PTVlcoAeySLsN8UZIrNc4X6UwoNIFrFY6zSn0xZSO_H9kNEt5FHK2mK0OZKha2UEq1Jd1cz88VqxQ1RB38t1meQg7hychw-uvPlZw](../../media/v_lG-PTVlcoAeySLsN8UZIrNc4X6UwoNIFrFY6zSn0xZSO_H9kNEt5FHK2mK0OZKha2UEq1Jd1cz88VqxQ1RB38t1meQg7hychw-uvPlZw.png)

Edit the database configuration by changing the following lines:

![w-RZOfaKxnPdg8dSP7Y282TfMRhmj4GJI3k9hFb7lchhgPtVKu-UxyrZDzf0c5ydb1sa2UceZT1relIn7j9tGl32ARBkosaWkEO0tO4](../../media/w-RZOfaKxnPdg8dSP7Y282TfMRhmj4GJI3k9hFb7lchhgPtVKu-UxyrZDzf0c5ydb1sa2UceZT1relIn7j9tGl32ARBkosaWkEO0tO4.png)

**DB_NAME**: your RDS database name

**DB_USER**: The name of the user you created in the database in the previous steps

**DB_PASSWORD**: The password for the user you created in the previous steps
**DB_HOST**: The hostname of the database means your database endpoint

The second configuration section you need to configure is the Authentication Unique Keys and Salts.

You can replace the entire content in that section with the below content:

    define('AUTH_KEY',         '@VZ<pXEL?vb-kiz(Zfp_R9f9|.+T-O/P$Z9|T-q%~|KX@,/(RZk00K{ybHA=6nT6')
    define('SECURE_AUTH_KEY',  '12Ip[Ts<IA>Vc+R#_X>i85OjMMRtks-o^E2(,$P[Q=f~Zt:@FrW1r$,` vqs|%@|');
    define('LOGGED_IN_KEY',    'o*_:obJ!+wtc8&]QhK}-xEVv+eVD!hFbBzkxKn@}(gK{-{d|l-?9b)8+)tfx8zjl');
    define('NONCE_KEY',        'Ue<fX0Z71vg7Y&F+~CqM-G%N~ozMe%?qrp-@|tTVh??zJ4:~Sm,VhTKBE0C7DY(?');
    define('AUTH_SALT',        'v.Z^1,QR66F-CDW=t<daxxk-;|M3cC{XzF`rn#l[U]f-fboHZYY/c8nvYU(uM`a]');
    define('SECURE_AUTH_SALT', 'Cz$[Mq>)Hc=BSo,&Q%;,r}Eu7!:>nj4N91WeIx|7jp=fc+S64lMXCNj|h&a9Q5[D');
    define('LOGGED_IN_SALT',   'Y{[of`B<!<<Za+|YtiMJkd33@a}+I%-0u}EPmAx?hW~$_(( u iuIJ2UQUJIv7(Q');
    define('NONCE_SALT',       'g<!-Nhqy2E{X{87!|x{Amg3v:Z%e8d(z3l9x|g-T uB62u4xuw?uyjS_>1Yl]~Kw');;

![bLVUCduPlqmY9ywcN7qArbxD4zGZlLtAF8THkB3Y9r-ckiNcY3sxZK5G_MAExeLtA9HLxnGHBea-gyr4lUjjgI_Ta1Sw9YeEmc3B3xv5](../../media/bLVUCduPlqmY9ywcN7qArbxD4zGZlLtAF8THkB3Y9r-ckiNcY3sxZK5G_MAExeLtA9HLxnGHBea-gyr4lUjjgI_Ta1Sw9YeEmc3B3xv5.png)

First, install the application dependencies you need for WordPress. In your terminal, run the following command.

    sudo apt install php libapache2-mod-php php-mysql -y

![KCChQ2inL90wSqDPavXUImzzRShV5ulwZIme7RGdjhcRy83gBNHOafvHU-XXI4EKP3CFW7VUrkMvOPnXSFXQb-na63Z6YxyXLFTr24YG](../../media/KCChQ2inL90wSqDPavXUImzzRShV5ulwZIme7RGdjhcRy83gBNHOafvHU-XXI4EKP3CFW7VUrkMvOPnXSFXQb-na63Z6YxyXLFTr24YG.png)

Copy your WordPress application files into the /var/www/html directory used by Apache.

    sudo cp -r wordpress/* /var/www/html/

![LERyvvQ6x97MJjWXN9pBb9ArMXkLBrkODZeG7eQCC3BwUOY6bb8lT8RGSPk-XJ9NUv_RAARMuWSUiXtYxphyqpfv6yte-GfoP3D1C0Lq](../../media/LERyvvQ6x97MJjWXN9pBb9ArMXkLBrkODZeG7eQCC3BwUOY6bb8lT8RGSPk-XJ9NUv_RAARMuWSUiXtYxphyqpfv6yte-GfoP3D1C0Lq.png)

Finally, restart the Apache web server

    systemctl restart apache2

Browse "ec2-public-ip/wp-admin/" you should see the WordPress welcome page.

![c1iK33HFFWMb7c3VnGD2h59rP5qpLRXbQzTW78GZJajcdA1j6muZggpVm7BPWO88CIRCoLby7bmAFI3vWBDRKaYhpE25YbTd95IP5Z0](../../media/c1iK33HFFWMb7c3VnGD2h59rP5qpLRXbQzTW78GZJajcdA1j6muZggpVm7BPWO88CIRCoLby7bmAFI3vWBDRKaYhpE25YbTd95IP5Z0.png)
