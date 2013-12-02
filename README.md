JSPHPLog
========

PHP Server side implementation for JSNLog (http://js.jsnlog.com/)

Uses the "error_log" command to save the log message from the JSNLog AJAX request to the default error log.

Example output:<br/>
[Tue Nov 26 15:43:22 2013] [error] [client xxx.xxx.xxx.xxx] [JSPHPLog]: This message sent from JSNLog, referer: http://*client site*/JSPHPLog/sample.php

<h3>Configuration options</h3>

  <p><b>Default</b></p>
  To use the default appender and logger, simply copy the "jsnlog.logger" and "jslog.config.php" files to your website root directory, then add an Apache handler directive (to either "httpd.conf" or ".htaccess") to process the .logger file as .php:
    
    <VirtualHost *:80>
    	...
    	<FilesMatch "\jsnlog.logger$">
    		SetHandler application/x-httpd-php
    	</FilesMatch>
    </VirtualHost>
    
   <p><b>Custom configuration (simple)</b></p>
   To customize the Appenders or Logger configuration settings, use Apache2 "SetEnv" directives inside \<VirtualHost\> to set the JSON options objects for both:
  
    <VirtualHost *:80>
    ...
	    SetEnv JLAppenderCfg {"level":2000,"batchSize":3}
	    SetEnv JLLoggerCfg {}
		<FilesMatch "\jsnlog.logger$">
	    	SetHandler application/x-httpd-php
	    </FilesMatch>
    </VirtualHost>
    
  jslog_config.php will look for the $\_SERVER["JLAppenderCfg"] and $\_SERVER["JLLoggerCfg"] variables and will set up the JSNLog Javascript accordingly.
