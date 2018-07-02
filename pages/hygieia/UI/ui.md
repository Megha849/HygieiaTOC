---
title: UI Configuration
tags:
keywords:
toc: true
summary: Learn how to build and run the Hygieia UI layer
sidebar: hygieia_sidebar
permalink: ui.html
---

[![Docker Stars](https://img.shields.io/docker/stars/capitalone/hygieia-ui.svg)](https://hub.docker.com/r/capitalone/hygieia-api/)
[![Docker Stars](https://img.shields.io/docker/pulls/capitalone/hygieia-ui.svg)](https://hub.docker.com/r/capitalone/hygieia-api/)

The UI Layer represents Hygieia's front-end and contains GUI elements for users to view and configure the DevOps tools on the dashboard.

The Hygieia dashboard requires installation of:

- NodeJS
- npm
- gulp
- bower

#### Mac OS X Installation

If you do not already have NodeJS installed, download and install the [NodeJS MSI package](https://nodejs.org/en/download/) for your platform.

*	**Step 1: Install Homebrew**
	
	Homebrew handles downloading, unpacking and installing npm on your system.
	To install Homebrew, open terminal and execute the following command:
	
	```bash
	ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	```
	
 	Follow the messages in the terminal to complete the installation process.
	
*	**Step 2: Install npm**
	
	To install npm using Homebrew, execute the following command:
	
	```bash
	brew install node
	```
	
	Configure the proxy settings for npm:
	
	```bash
	npm config set http-proxy http://username:password@proxy.company.com:8080
	npm config set https-proxy http://username:password@proxy.company.com:8080
	```
	
*	**Step 3: Install Global Packages**
	
	Execute the following commands to install packages to the global `node_modules` directory:
	
	```bash
	npm install -g bower
	npm install -g gulp
	```
	Install dependencies configured with bower and npm:
	
	```bash
	# Install dependencies listed in package.json
	npm install
	# Install dependencies listed in bower.json
	bower install
	```
	
*	**Step 4: Run the UI**
	
	In the terminal, navigate to the `/Hygieia/UI` and execute the following command:
	
	```bash
	gulp serve
	```
	
	The dashboard will serve up on port 3000.
	
#### Windows Installation

If you do not already have NodeJS installed, download and install the [NodeJS MSI package](https://nodejs.org/en/download/) for your platform.

*	**Step 1: Install npm**

	Execute the following commands using command line to install bower and gulp globally:

	```bash
	npm install -g bower
	npm install -g gulp
	```
	
	From your project's root directory, use Git Shell to install bower using the following command:

	```bash
	# Install dependencies listed in bower.json
	npm install
	# Install dependencies listed in bower.json
	bower install
	```

*	**Step 2: Run the UI**

	To run the dashboard, in the command prompt, go to `\Hygieia\UI`, and then execute the following command:

	```bash
	gulp serve
	```
	The dashboard will serve up on port 3000.

	To execute using browser-sync's [`ghostMode`](https://www.browsersync.io/docs/options#option-ghostMode) functionality:

	```bash
	gulp serve:ghost-mode
	```

	To run using Maven, go to `\Hygieia\UI`, and then execute the following command:

	```bash
	mvn clean package integration-test
	```
#### Test UI Layer Locally

To test Hygieia's UI layer locally using mock test data, execute the following command:

```bash
gulp serve --local true
```
In this case, API is not required since data currently comes from the test-data directory.

### Docker Image for UI Layer

To configure the Hygieia UI layer, execute the following steps:

*	**Step 1: Run Maven Build**

	To package the API source code into an executable JAR file, run the maven build from the `\Hygieia` directory of your source code installation:

	```bash
	mvn clean package -pl UI docker:build
	```
	
*	**Step 2: Run the UI**

	To run the UI from Docker, execute the following command from the command prompt:
	
	```bash
	docker run -t -p 8088:80 --link hygieia-api -i hygieia-ui:latest
	```
	
### Dashboard Layouts

Select a layout for your dashboard. Layouts for the dashboard are available at `src\components\templates`. You can choose a custom template or customize your dashboard layout by selecting widgets while creating your dashboard. The available custom templates are:

* Cap One
* Cap One ChatOps
* Cloud Dashboard
* Split View

### API Check

Once the UI is successfully connected, the following screenshots show the API connection status:

**Login page with API layer successfully connected**

![Image](http://capitalone.github.io/Hygieia/media/images/apiup.png)

**API layer connection unsuccessful**

![Image](http://capitalone.github.io/Hygieia/media/images/apidown.png)

**Signup page to create admin user**

![Image](http://capitalone.github.io/Hygieia/media/images/adminuser.png)

