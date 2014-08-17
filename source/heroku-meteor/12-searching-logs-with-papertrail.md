<link href="index.css" rel="stylesheet" type="text/css">

# <a id="top">Chapter 12: Searching Logs with Papertrail</a>

  **Goal**: This chapter will teach you how to add the Paptertrail Heroku Add-on to your application.  Papertrail provides a robust web interface for searching your application's logs and setting alerts for specific searches.

To add the Papertrail Add-on:

1. Navigate in your browser to [https://addons.heroku.com/papertrail](https://addons.heroku.com/papertrail)
2. Select `Add` for the free "Choklad" level of service
3. Select your application from the drop-down
4. Select `+`
5. Open the `Add-ons` drop-down for your application
6. Select `Papertrail`

After a minute or so Papertrail will have your latest logs.

Enter a search term like `WARN` in the search box at the bottom of the screen.  You will then see all of the log entries for your application which match that term.

You can setup Papertrail to notify you via email when new log entries matching your search are received:

1. Select `Save Search`
2. Enter a name for the saved search
3. Select `Save & Setup Alert`
4. Select `Emails`
5. In the `Recipients` field enter your email address
6. Choose a `Frequency`
7. Select `Update`

The next time your application has a log event that matches your search, you will receive an email notification.

[Back to top...](#top)

[Back to Workshop home](index.html)

