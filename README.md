#Getting Started
Using vagrant will allow us to work with each other in the same environment, so that's what we will use. Getting Started is designed to help you get ready for hack night on the week of the 27th. This will be updated after hack night as a resource for future reference. This does take a quite a while (especially with slower internet), which is why I'd like for it to be taken care of beforehand. I will go through and explain this process at hack night, although it may be pretty straightforward for you.

###Installation
Download and install vagrant from Vagrant [downloads](https://www.vagrantup.com/downloads.html) page

Download and install Virtualbox AND Virtualbox Extensions from the Virtualbox [downloads](https://www.virtualbox.org/wiki/Downloads) page (Virtualbox must be installed before Virtualbox Extensions can be)
###Setup
Create a folder and navigate to it (this will house your Vagrantfile and another folder that your project will actually be in)

Run the following command
```
vagrant init ubuntu/trusty64
```

Open Vagrantfile in your favorite text editor

Look for the following line:
```ruby
  # config.vm.network "forwarded_port", guest: 80, host: 8080
```
This allows you to forward a port on the guest(vagrant) to a port of your choosing on the host(your computer)

Add the following line below (make sure you have 2 spaces as your indentation)
```ruby
  config.vm.network "forwarded_port", guest: 7000, host: 7000
```

###Start vm
Run
```
vagrant up --provider virtualbox
```
This creates, or boots, a Virtualbox vm. It will take some time as it will need to download ubuntu.

###Access vm
```
vagrant ssh
```

##Ubuntu setup
```
sudo apt-get update
sudo apt-get install -y build-essential checkinstall libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev git
sudo apt-get install -y python3 python3-pip nodejs php5 php5-mcrypt
exit
```

###Shutdown vagrant box
```
vagrant halt
```

###Clone this repo
```
git clone https://github.com/byudevelopers/backend-demo.git
```
Or if you prefer ssh:
```
git clone git@github.com:byudevelopers/backend-demo.git
```

You are now ready for hack night(:
If you get stuck anywhere, do not hesitate to ask me in slack, or create an issue in this repo.

You can stop here, but are definitely welcome to look further. I will be going over it at hack-night though.

#[Vagrant](https://www.vagrantup.com/)
Vagrant creates a desktop environment that can be shared with team members so you are testing within the same environment.

I like it because it's something that I can completely mess up to figure out what I'm doing, then destroy it and spin up a new vm when I have a better idea of what's going on. Another benefit for me is that I can actually use the same environment that I'll be deploying to. This way I know it will work when I put it into production. That being said, I have never really dived into all that you can do with vagrant. I've also tried to use Docker and failed miserably at figuring it out, but it seems like vagrant is the right fit for my purposes anyways.

##Crash course on vagrant
```
vagrant up
```

Starts the vagrant box/vm

```
vagrant ssh
```

Opens an ssh tunnel into your

```
vagrant reload
```

Reloads your vm with any changes made to your Vagrantfile

```
vagrant halt
```

Shuts down your box

```
vagrant destroy
```

TODO- add sharing

Shuts down and deletes your vm

The Vagrantfile is what vagrant uses to initialize a virtualbox (or other vm provider) vm. There are other tools you can use to extend the use of Vagrantfile, through [provisioning](https://www.vagrantup.com/docs/provisioning/), but we will not be going into that (mostly because I've never had a use for it and don't know a whole lot about it). Take a look at your Vagrantfile. It is actually really well commented and pretty much explains itself.

#Q&A
What is a package manager?

It is exactly what it says it is. Packages, or modules, are stored in a central location. The package manager stores (sometimes not) and allows users to download packages as needed.

What is a framework?

A framework is an abstraction that provides commonly used code to a developer (helps to reduce code duplication). Frameworks also control the application's flow and is generally extendable/overridable. It could also be considered a scaffold used to start a project from. A good way to conceptualize the idea is to think about making sugar cookies as a kid. Your mom would have some cookie cutters for you to pick from. You would then pick one and use it as the "framework" for cutting the remainder of your cookies, rather than getting a knife out and having to cut each edge precisely to get the design that you are looking for.

###Questions?

Ask them at hack night or in the issues of this repository.

#[Node](https://nodejs.org/en/)
Node is Javascript on the server side, which is pretty cool! It leverages Chrome's V8 Javascript engine.  It is event driven, asynchronous, super fast, scalable, single threaded, cross-platform, and open source. It can be used to build web applications, desktop applications, and CLI tool. To start a Node app just type `node <filename>.js` -or- `nodejs <filename>.js` depending on how you installed it.

What is it good for?
* I/O Bound Applications
* Data Streaming Applications
* Data Intensive Real time Applications (DIRT)
* JSON APIs
* Single Page Applications (ajax)
* Static file servers
* CLI Tools
* Distributed Systems
* ...

What is it not good for?
* CPU intensive Applications
* Basic CRUD/HTML apps (Well, its just not better than anything else)
* Teams that do not have JS experience

Sources (in no particular order):
* <http://www.tutorialspoint.com/nodejs/nodejs_introduction.htm>
* <http://stackoverflow.com/questions/4531649/what-exactly-is-node-js-used-for>
* <https://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js>
* <https://medium.com/@ivanguardado/node-js-the-bad-parts-b4b9d23ef7e2#.ec6wr6god>
* <https://www.sitepoint.com/node-js-is-the-new-black/>
* <http://stackoverflow.com/questions/1884724/what-is-node-js>

##[npm](https://www.npmjs.com/)
npm is Node's package and dependency manager.

npm uses a file called package.json to keep track of what packages and dependencies are needed to run a node application. A package.json looks like this:

```json
{
  "name": "node",
  "version": "0.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "BSD-2-Clause",
  "dependencies": {
  }
}
```

You do not need to type this in yourself, npm will auto-generate it by running:
```
npm init
```

npm then prompts you to answer a few questions (you can just keep pushing enter unless you care), and then you are good to go. Just type in `npm install <package-name>` to get the module.

There are a 2 important flags for `npm install`

```
npm install --save
```

This will save the package as a dependency for the project you are working on

```
npm install --save-dev
```

This will save the package as a devDependency for the project you are working on. devDependencies are only needed in development, ie. minifier

If you do not use these flags, the package is globally available. [Learn more about these flags](https://docs.npmjs.com/cli/install)

##[Express](http://expressjs.com/)
The most popular NodeJs lightweight, modular web application framework. It is extended with the use of modules and is generally used for secure/rapid development. [Learn more](https://stackoverflow.com/questions/12616153/what-is-express-js)

##Basic NodeJs/Express app:
Access your box
```
vagrant up  # if not running
vagrant ssh
```

First, we need to install Node and npm.
```
sudo apt-get install node
sudo apt-get install npm
```
It is always a good idea to read the [documentation](http://expressjs.com/en/api.html)

There is actually a 'better' way of doing this: nvm (Node Version Manager). I'm going to keep things simple and not use it, but know that it is recommended.

Lets initialize our node project
```
npm init
```

Press enter until the prompt no longer asks for information (this can all be filled out later). You should see a package.json file in the directory. If not, try it again.

Install Express next

```
npm install --save express
```

This will create a folder called node_modules that your dependencies will be downloaded to. Express will also be added to the dependencies in package.json.

You are now ready to get started!

In the app.js file, type the following:

```javascript
// Load express
var express = require('express');

// Create an express app
var app = express();

// Create a HTTP GET route for the root url(/)
//  -- This is what will appear when you navigate to the base url
//  (ie. <https://www.google.com>, <http://localhost:7000> for us)
app.get('/', function(request, response) {
    response.send("Hello world")
})

// Set up the app to listen on port 700
app.listen(7000, function() {
    // Print something so you know the app is running
    console.log("App is running on port 7000")
})
```

Type `nodejs app.js` into the terminal and you should see `App is running on port 7000` in the terminal. Navigate to <http://localhost:7000> in your browser. If all is well, Hello world will appear in your browser.

#[Php](https://secure.php.net/)
Php is an open-source, easily scalable, general-purpose scripting language. It is widely-used, odds are you will use php at some point in your life (more likely as legacy code). There are a lot of php frameworks. Php was actually never meant to be a programming language, it just kind of turned out that way. That being said, php has fantastic documentation and a ton of integrations. Php gets a lot of flack, but it's actually has reasonable performance and is super easy to pick up if you know any C based language. You can run php in a LAMP stack (with an apache server). This has been the development and production environment for php until recently. You can now use php's built in server by running `php -S localhost:7000 -t .`

Wordpress and Drupal are built on Php and makes building a website easier with plugins and the ability to customize the look/feel of your site.

Sources:
* <https://secure.php.net/manual/en/intro-whatis.php>
* <https://secure.php.net/manual/en/intro-whatcando.php>
* <https://en.wikipedia.org/wiki/PHP>

What is it good for?
* Web Development
* Web API

What is it not good for?
* Pretty much everything else

##[Composer](https://getcomposer.org/)
Php's dependency manager. [Learn more](https://scotch.io/tutorials/a-beginners-guide-to-composer)

Like npm, composer uses a json file to keep track of dependencies (composer.json). It looks like this:

```json
{
    "name": "username/my_project",
    "description": "My New Project",
    "authors": [
        {
            "name": "Joe Mama",
            "email": "mail@mymail.com"
        }
    ],
    "require": {
    },
    "require-dev" : {
    }
}
```

Adding packages is as simple as:
```
composer install <package-name>
```

Composer can also install packages directly from github.

We won't actually be using composer, it's beyond the scope of our needs. It's ony used to install "middleware" which is the php equivalent of packages/modules. We won't actually be using any middleware, so if you are interested in learning composer, it is just as easy as the other package managers.

To install Composer on Ubuntu:
```
sudo apt-get install curl php5-cli git -y
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
sudo php composer-setup.php
php -r "unlink('composer-setup.php');"
```
Composer dependencies are installed in a generated folder called vendor

##[CodeIgniter](https://www.codeigniter.com/)

Download CodeIgniter from [here](https://www.codeigniter.com/download)

We only really need index.php, the system folder, and the application folder to make a functioning app. From within the CodeIgniter folder, start the app by running `php -S localhost:7000 -t .`

This auto-loads the index file. Within the index file, all settings are generated. The application and system folders are also added to the app. The system folder contains core functionality of CodeIgniter and the application folder is the actual application. 

Within the application folder your have several subfolders. The folders that are of most interest to us are: config, controllers, and views. 

Routes are setup in application > config > routes.php. 

```php
$route['default_controller'] = 'welcome';
```
This is a route. default_controller indicates that this is the default/root uri (localhost:7000). For the localhost:7000/hi url, just add a new entry:

```php
$route['hi'] = 'hi';
```

By adding a route to the associative array, you are basically saying: when someone goes the the /hi uri (`$route['hi']`), then I want you to use the hi controller. Navigate to application > controllers > Welcome.php to view the default controller `welcome`. You can create the hi view by creating a Hi.php file and adding the following:

```php
<?php
defined('BASEPATH') OR exit('No direct script access allowed');

class Hi extends CI_Controller {

  // This is the function that CodeIgniter calls when a user accesses the route
  public function index() 
  {
    $this->load->view('hi'); // Load the hi view
  }
}
```


Navigate to application > views welcome_message.php to see the default route's view. Php is supposed to be the fastest templating engine, although I'm not sure I believe that. What you are seeing is a php staticly rendered page. Our page is going to be much simpler then that. Add hi.php to views and enter in the following:

```php
<!DOCTYPE html>
<html>
<head>
    <title></title>
</head>
<body>
<?php echo 'hi'; ?>
</body>
</html>
```

If you now navigate to localhost:7000/hi you will see your new view!

CodeIgniter is unlike any of the other frameworks here. While it is much more opinionated and robust, it is still a light framework as far as php frameworks go. [Slim](http://www.slimframework.com/) and [Lumen](https://lumen.laravel.com/) are more similar to Express. You only get an extendable micro-framework that does very little heavy lifting. Middleware can also be added to handle things like sessions and authentication, but you must add them yourself, and come up with your own code structure (MVC/MVP/etc)

#[Python](https://www.python.org/)
Python is an interpreted, object oriented language. It is really easy to learn and use, it's also my favorite(: It has a large standard library that is easily extendable. Modules can be written in C/C++ for performance (this is the same for Node/ruby, just more commonly used in python). It is also cross-platform and has an extremely dynamic use case. It comes with a built in sandbox (called IDLE) that can be accessed anywhere by typing `python` into the terminal. `python <filename>.py` will start a python app.

What is it good for?
* Prototyping
* Data Science
* Machine Learning
* Data Mining
* Web Development
* Scientific and Numeric Computing
* Education
* Desktop Applications
* GIS
* CLI/scripting
* Testing
* API's
* ...

What is it not good for?
* Real time apps 
* CPU Bound aplications
* Heavy graphic games
* ...

Sources:
* <https://www.python.org/doc/essays/blurb/>
* <https://www.python.org/>
* <https://wiki.python.org/moin/BeginnersGuide/Overview>
* <https://www.reddit.com/r/Python/comments/23ap65/what_kind_of_project_would_you_not_use_python_for/>
* <https://programmers.stackexchange.com/questions/15468/what-are-the-drawbacks-of-python>
* <https://www.reddit.com/r/Python/comments/1r1yke/what_do_you_use_python_for/>
* <https://www.quora.com/What-is-Python-mainly-used-for-in-the-real-world-today>

##[pip](https://pypi.python.org/pypi/pip)
pip is the Python Package index. This is a dependency and package manager for python.

You can install modules with:

```
pip install <package-name>
```

pip uses a file typically called requirements.txt to keep track of packages installed. It is best practice to use a virtual environment to keep track of packages that have been installed for a specific project.

Install virtualenv with:
```
pip install virtualenv
```

In your project's directory (or wherever you want to create it) enter in:
```
virtualenv venv
```

You can name your virtualenv anything you'd like, I just always name it venv.

Then, to use the virtualenv type:

```
source venv/bin/activate
```

You are now in a virtualenv. Anything you pip install will only exist in this environment. You can then create a requirements.txt file. To save the state of your virtualenv, just type the following in the same directory as requirements.txt
```
pip freeze > requirements.txt
```

To install from the requirements.txt file, you simply type `pip install -r requirements.txt`

Just an FYI, we will be using python3. So, instead of pip, you will type pip3.

Python3 is the most current, stable, version of Python. This is why we will be using it. 

##[Flask](http://flask.pocoo.org/)

#[Ruby](https://www.ruby-lang.org/en/)
A dynamic, reflective, pure object-oriented, general purpose, open source scripting language written by a Mormon. Its syntax is designed for simplicity and productivity. It is not built for high performance. It is most known for Ruby on Rails (the web framework) which has a fantastic approach to MVC. Just like the other scripting languages, you execute a ruby application with `ruby <filename>.rb`

Sources:
* <https://en.wikipedia.org/wiki/Ruby_(programming_language)>
* <https://www.ruby-lang.org/en/>
* <http://ruby.about.com/od/beginningruby/a/WhatIsRuby.htm>

What is it good for?
* Text processing
* Web Development
* Large Software Systems
* Provisioning tools
* CLI tools
* ...

What is it not good for?
* Anything that requires performance
* ...

##[gem](https://rubygems.org/)
RubyGems is Ruby's package manager. To install a ruby package just use:

Ruby dependencies are managed through a gemfile [learn more](http://bundler.io/v1.5/gemfile.html)

Gemfiles look like this:
```
source 'https://rubygems.org'

gem 'nokogiri'
gem 'rails', '3.0.0.beta3'
gem 'rack',  '>=1.0'
gem 'thin',  '~>1.1'
```
Or this:
```
source 'https://rubygems.org'

gem 'wirble', :group => :development
gem 'debugger', :group => [:development, :test]
```
Or this:
```
source 'https://rubygems.org'

group :test do
  gem 'rspec'
end
```

Install packages with:

```
gem install <package>
```

##[Sinatra](http://www.sinatrarb.com/)
