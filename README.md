# Install Phalcon 3.4.0 with MAMP Pro 5 on a macOS High Sierra
Instructions on how to succesfully create a local development enviroment for Phalcon PHP Framework in a Mac. It aims to save others precious time that spent trying to get a working enviroment as of 2019-05-14.

After much trial and error this is the combination I was able to fully get after hacking thru an array of errors and road blocks.
- MAMP Pro 5
- PHP 7.2.14 (MAMP Pro Version)
- Phalcon 3.4.0

## Install MAMP Pro 5
- Download and install MAMP Pro 5
https://www.mamp.info/en/mamp-pro/

## Create a VirtualHost for your phalcon site
- Click on hosts
- Add a VirtualHost by clicking + sign 
- Enter "Name" (phalcon)
- Select a "Document root" (/Code/phalcon)

## Create PHP Info file
- In your favorite browser create an index.php file
- Add the following line phpinfo(); 
- Save

## Change PHP Version
- Under languages click on PHP
- Change Default version to 7.2.14
- Check "Make this version available on the command line"
- Restart web server

## Setup local PHP to your MAMP Pro PHP
- Assuming your are using bash open your local bash profile config file
`vi ~/.bash_profile`

- Add the following line to include MAMP PHP 7.2.14 version in your path
`export PATH=/Applications/MAMP/bin/php/php7.2.14/bin:$PATH`

- Save and quit the file
`ESC + shift + z z`

- Source the bash profile
`source ~/.bash_profile`

## Install php-psr
- In the terminal go your source root 
`cd /Code`

- Clone php-psr 
`git clone git@github.com:jbboehr/php-psr.git`

- Go inside your php-psr repo 
`cd php-psr`

- Since we are using an specific (MAMP PHP 7.2.14) run the specific phpize
`/Applications/MAMP/bin/php/php7.2.14/bin/phpize`

- Configure php-psr with PHP 7.2.14 specific php-config
`./configure --with-php-config=/Applications/MAMP/bin/php/php7.2.14/bin/php-config`

- Compile
`make`

- Test
`make test`

- Be a good human and submit your test the PHP QA team
Do you want to send this report now? [Yns]: `Y`

- Install php-psr
`sudo make install`

<!-- - Find your local CLI PHP file
`php -i | grep php.ini`

- Add php-psr to your local CLI PHP config file
`echo extension=psr.so | tee -a /Applications/MAMP/bin/php/php7.2.14/conf/php.ini` -->

- Add php-sr to your MAMP PHP Config file
- - In MAMP click on PHP under Languages
- - Click the arrow next to "Manually enable other extensions"
- - Go to the end of the file and add the following
```
[psr]
extension=psr.so
```

## Install phalcon
- Download the pre-compiled phalcon.so
`https://github.com/majksner/php-phalcon-mamp/blob/master/php7.2.1/phalcon.so`

- Copy the downloaded phalcon.so to your PHP 7.2.14 extensions directory
`/Applications/MAMP/bin/php/php7.2.14/lib/php/extensions/no-debug-non-zts-20170718`

<!-- - Add php-psr to your local CLI PHP config file
`echo extension=phalcon.so | tee -a /Applications/MAMP/bin/php/php7.2.14/conf/php.ini` -->

- Add php-sr to your MAMP PHP Config file
- - In MAMP click on PHP under Languages
- - Click the arrow next to "Manually enable other extensions"
- - Go to the end of the file and add the following
```
[phalcon]
extension=phalcon.so
```

## Install phalcon-devtools
- Go insinde Document Root
`cd /Code/phalcon`

- Clone the phalcon-devtools repo
`git clone https://github.com/phalcon/phalcon-devtools.git`

- Open your bash profile file
`vi ~/.bash_profile`

- Add the following aliases to your bash profile
```
export PTOOLSPATH=/Code/phalcon/phalcon-devtools/
export PATH=$PATH:/Code/phalcon/phalcon-devtools
alias phalcon=/Code/phalcon/phalcon-devtools/phalcon.php
```

- Save and quit
`ESC + shift + z z`

- Reload your bash profile
`source ~/.bash_profile`

- Test that phalcon is working from your command line
`phalcon`

- The following output should appear
```
  Phalcon DevTools (3.4.0)

  Available commands:
    info             (alias of: i)
    commands         (alias of: list, enumerate)
    controller       (alias of: create-controller)
    module           (alias of: create-module)
    model            (alias of: create-model)
    all-models       (alias of: create-all-models)
    project          (alias of: create-project)
    scaffold         (alias of: create-scaffold)
    migration        (alias of: create-migration)
    webtools         (alias of: create-webtools)
    serve            (alias of: server)
    console          (alias of: shell, psysh)
```
## Pray and give the 'Higher Power' of your understanding praises
- It only took me half a day to get here :sweat:

## Create your first phalcon project
- Go to your Document Root
`cd /Code/phalcon`

- Create your first phalcon project
`phalcon create-project test`

- Point your browser over to your new phalcon project
`http://phalcon:8888/test`

# :-o HOLLY MACRO! 

## Donate
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=AU9HLKVAFNPQ8)
