# php_mail

Another PHP mail wrapper lib


## Adapters

* [Swiftmailer](http://swiftmailer.org/) - Supports SMTP, sendmail, postfix, server username/password and encryption.


## Install

Clone and init submodules.

	git clone --recursive git://github.com/Znarkus/php_mail.git


## Setup

This example uses the Swiftmailer adapter.

	require 'lib/abstract.php';
	require 'lib/swift.php';
	require 'lib/factory.php';

	$factory = new Lib\Mail_Factory('swift', 
		array('host' => '127.0.0.1', 'port' => 25, 'from' => array('address' => 'from@example.com', 'name' => 'Markus')
	);


## Basic usage

	$factory->create()
		->subject('Testing')->body("Body\nNew line")->to('to@example.com')->send();


## Templating

Templates could be stored in files and loaded with [file_get_contents()](http://php.net/manual/en/function.file-get-contents.php),
or with some template engine.

	$tpl = "
	SUBJECT
	This is the subject

	PLAIN BODY
	This is the mail body
	spanning
	multiple lines.
	";

	$factory->create()
		->template($tpl)->to('to@example.com')->send();


## License

Copyright 2012, [Markus Hedlund](http://markushedlund.com), [Snowfire](http://snowfireit.com)  
Licensed under the MIT License.  
Redistributions of files must retain the above copyright notice.