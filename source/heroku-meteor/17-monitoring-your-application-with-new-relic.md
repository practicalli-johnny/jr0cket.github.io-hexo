<link href="index.css" rel="stylesheet" type="text/css">

# <a id="chapter6">Chapter 6: Performance Monitoring with New Relic</a>

  Goals: With the New Relic Heroku Add-on you can easily setup application performance monitoring and reporting.  This chapter will teach you how to add New Relic to your application.

  New Relic provides an in-depth view into the performance and memory usage of applications on Heroku.

Start by adding the New Relic Add-on:

1. Navigate in your browser to [https://addons.heroku.com/newrelic](https://addons.heroku.com/newrelic)
2. Select `Add` for the free "Standard" level of service
3. Select your application from the drop-down
4. Select `+`

Now your application needs to be configured to use the New Relic Java agent:

1. Download the newest New Relic Java Agent zip file from [http://download.newrelic.com/newrelic/java-agent/newrelic-api/](http://download.newrelic.com/newrelic/java-agent/newrelic-api/)
2. Unzip the archive
3. Copy the `newrelic.jar` and `newrelic.yml` files into the root directory of your project

Commit these new files to your Git repository and push the new version to Heroku:


  You need to change the default `JAVA_OPTS` environment variable for your application to the Java process to use the New Relic Java agent.

1. In Eclipse, in the `My Heroku Applications` view select the application's context menu
2. Select `App Info`
3. Select the `Environment Variables` tab
4. Select the environment variable with the key of `JAVA_OPTS`
5. Select `Edit`
6. In the `Value` field enter `-Xmx384m -Xss512k -XX:+UseCompressedOops -javaagent:newrelic.jar`
7. Select `OK`

Test the application on Heroku in your browser and verify that it works as expected.

You can now browse the New Relic Dashboard:

1. In your browser navigate to [https://api.heroku.com/myapps](https://api.heroku.com/myapps)
2. Select the application you added New Relic to
3. Select the `Add-ons` drop-down
4. Select `New Relic`

Explore the New Relic dashboard.  (Note: It might take a few minutes for some data to appear in the dashboard.)


[Back to top...](#top)

[Back to Workshop home](index.html)

