---
layout: post
title:      "Using ProgreSQL with Rails on Windows"
date:       2020-07-15 01:29:38 -0400
permalink:  using_progresql_with_rails_on_windows
---


There can be some challenges that arise while using Windows for web development when much of the documentation is targeted for Mac users. This is particularly noticeable when needing to set up the various tools that we use for web development.

![](https://img.memecdn.com/mac-vs-pc_o_702002.gif)

In this case I would like to share the insights I have gained while working through setting up PostgreSQL on Windows, as I found documentation for this to be quite lacking.

![](https://media3.giphy.com/media/Ln2dAW9oycjgmTpjX9/giphy.gif?cid=ecf05e47eb7b052478b63292f05b8b6fe28c66ecfa1fe0e6&rid=giphy.gif)

***
If you are starting fresh, you will need to install PostgreSQL. They currently provide their Windows installations at https://www.postgresql.org/download/windows/. At the time of writing this, the latest version available is 12.3.

Once downloaded, you can start the installer. Follow the promptings of the installer, ensuring that you leave the port number as 5432 and note the password that you create. At the end it will launch application stack builder, but, as this is not relevant to us at the moment, you can just close it.

***
Now that PostgresSQL is installed, we can switch to working with starting and configuring our rails application. In your terminal, you should type `rails new sample-project-name --database=postgresql`. Now that you have your basic files for your application, you will want to open them in the editor of your choice and navigate to `database.yml`, which is in the config folder.

***
Under the Development section of this file you will want to uncomment the rows with `username`, `password`, and `host`. If you used the default username in installation, you want to set this to `postgres`.

As for setting the password, you could type it into the file directly, but I highly recommend adding `gem 'dotenv-rails', groups: [:development, :test]` to your `Gemfile`, and then adding a `.env` file to the top layer of your folder. In this `.env` file you can store your password by setting it equal to what is between the brackets that follow ENV. And lastly, but importantly, add `.env` to your `.gitignore` file. There are plenty of great resources out there for diving into the use of dotenv though.

***
Under the same development heading in the database.yml file, you will want to note what database is set to. We can now continue to the last step. Open up the PostgreSQL Admin tools, called pgAdmin 4. Once you have opened this up in your browser and entered the relevant password, you will want to expand the items on the left, until you reach and select databases. Now, clicking on Object in the menu bar, you will want to open Create > Database… In the pop-up all you have to do is enter the database name you noted earlier and save.

This should now have you successfully up and running with PostreSQL for Rails on a Windows machine.


**;tldr**
* Install PostgreSQL
* Create Rails project with PostgreSQL as the database
* Modify database.yml file
* Create the relevant database through admin tools
* Enjoy!
