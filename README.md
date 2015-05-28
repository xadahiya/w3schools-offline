# w3schools-offline

#OFFLINE version of W3Shools.
W3Schools is a web developer information website, with tutorials and references relating to web development topics such as
HTML, CSS, JavaScript, PHP, SQL, and JQuery. The site provides a reference manual covering many aspects of web programming.

# Ubuntu Instructions

 You need to setup an Apache server as w3schools use #asp engine, which cannot be rendered directly by the browser.

 Creating server for ASP.NET applications in Ubuntu using Modmono
  ModMono is an Apache module which provides ASP.NET support for Apache web server. We will be using Apache as an        alternative for Microsoft’s IIS in Windows.
  
  # Installation
  Here is a nice tutorial to setting up the server, just follow its #installation part          https://ubuntuexperiment.wordpress.com/2009/01/29/running-aspnet-applications-in-ubuntu-using-modmono/

  # Adding the offline website
  We are going to create a site called W3schools. But first we need to create a configuration file for this site inside    the directory “etc/apache2/sites-available/”. To do this, execute the following command:
  
  sudo nautilus /etc/apache2/sites-available/ 
  
  This will open the directory in Nautilus. Now right-click inside the window and create a new empty file and name it “W3schools.conf”. Then open the file using a text editor and paste the following text inside it, save and close.
  
    Alias /W3schools "/var/www/W3schools"
    AddMonoApplications default "/W3schools:/var/www/W3schools"
    <Location /W3schools>
    SetHandler mono
    </Location>
    
  You need to change the server root directory for W3schools to successfully work.
    Run the command 
    
    sudo gedit /etc/apache2/sites-available/000-default.conf
    
  and change the following line to what you want:

    DocumentRoot /var/www/html to /var/www/W3schools
  
  Also edit apache2.conf to do so run 
    sudo gedit /etc/apache2/apache2.conf
    
    and find this
      <Directory /var/www/html/>
      Options Indexes FollowSymLinks
      AllowOverride None
      Require all granted
      </Directory>
      
 and change /var/www/html to your preferred directory( /var/www/W3schools )


  Now inside Nautilus, browse to /var/www/ directory and create a new folder called “W3schools”
  
2.Download and extract the zip file from the link below:

https://drive.google.com/file/d/0BxNDMvWYfeVEOUpOU1cwSndfVFU/view?usp=sharing


Then come the final steps where we enable the site and restart Apache one last time:

    a2ensite Ubuntu
    sudo /etc/init.d/apache2 restart
    
That’s it! Now open your web browser and point to:
http://localhost/W3schools/index.html

#Windows instructions

#part 1
On the Start menu, click Settings and select Control Panel

Double-click Add or Remove Programs

Click Add/Remove Windows Components

Install Internet Information Services (IIS)

Look for a new folder called Inetpub on your hard drive( windows installation drive )

Open the Inetpub folder, and find a folder named wwwroot

#part 2

  7. Download and extract the following file
      https://drive.google.com/file/d/0BxNDMvWYfeVEOUpOU1cwSndfVFU/view
  8. Copy the contents from the folder www.3schools.com to wwwroot folder ( just copy the contents of the folder not the folder)
  9. On the Start menu, find and open Internet Information Services (IIS)
  10. Find Default Web Site under sites on the left side
  11. Select the MIME type
  12. Add new from the right side
  13. Set File name extenstion to .asp and MIME type to text/html
  14. Save and exit
  15. Open the link in browser - http://localhost/index.html

#Enjoy!!!    

#Credits - W3schools.com
