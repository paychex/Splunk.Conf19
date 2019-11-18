# Splunk.Conf19

## Welcome!

###### Please note the this project was built and tested on Splunk Enterprise/Cloud version 6.6.* and above, due to the use of the union command.


Here you will find Splunk queries presented at Splunk .Conf19 in the presentation by Dustin Marling and Eric D. Favreau:

**FN1315 - Cover Your Assets: Protect Your Knowledge Objects from Yourself (and Others) - A Paychex story**

The presentation slides and video are available here: https://conf.splunk.com/watch/conf-online.html?search=FN1315#/

These queries are turnkey (almost). Meaning, depending on the query, you may need to edit a value or three to fit your circumstance and/or your environment. These are covered in the presentation, but we have a few gotchas to look for out of the gate.

Some queries reference a lookup file, MyCYA.csv. To create that file, end any export query with a line such as:
```
| outputlookup MyCYA.csv append=true
```
or
```
| outputlookup MyCYA_MLTK.csv append=true
```
etc.

In each query, watch for places where you need to use YOUR values for
- a lookup file
- search term
- auth token
- your splunk instance (unless it really is localhost)

With the Audit query, when getting started, you may want to remove line 29, to play with it. Line 29 gets only where the user and author are not the same. It's good for alerts.

We've seen issues having Splunk email the export results via the sendemail command or via a scheduled search. It had extra character sequences. YMMV. 

## Future Support
Ask questions at [Splunk Answers](https://answers.splunk.com/), so the whole community can benefit.
You may want to tag [@dmarling](https://answers.splunk.com/users/468259/dmarling.html) and [@efavreau](https://answers.splunk.com/users/251903/efavreau.html) in your question or comment, to get our attention.

Pull requests will be reviewed, however:

- It MUST be able to be used on a freshly downloaded version of Splunk
- You must specify the version of Splunk you used to test (for troubleshooting in case of issues with command deprecation or bugs, etc.)

## Additional Notes
Reference: https://answers.splunk.com/answers/780617/paychexsplunkconf19-cover-your-assets-cya-export-e.html
Note: It is safe to ignore the "Failed to parse templatized search for field" errors for any field originating from the ntags end point, that starts "tagged.*"
