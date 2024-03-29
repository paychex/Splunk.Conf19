# Splunk.Conf19

## Welcome!

###### Please note the this project was initially built and tested on Splunk Enterprise/Cloud version 6.6.*, due to the use of the union command. We, and many others, continue to use this solution on all subsequent versions of Splunk.


Here you will find Splunk queries presented at Splunk .Conf19 in the presentation by Dustin Marling and Eric D. Favreau:

**FN1315 - Cover Your Assets: Protect Your Knowledge Objects from Yourself (and Others) - A Paychex story**

The presentation slides are available [here](https://conf.splunk.com/files/2019/slides/FN1315.pdf) and the video is available [here](https://conf.splunk.com/files/2019/recordings/FN1315.mp4).

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
Ask questions at the [Splunk Community](https://community.splunk.com/) site, so the whole community can benefit.
You may want to tag [@dmarling](https://community.splunk.com/t5/user/viewprofilepage/user-id/215385) and [@efavreau](https://community.splunk.com/t5/user/viewprofilepage/user-id/88735) in your question or comment, to get our attention.

Pull requests will be reviewed, however:

- It MUST be able to be used on a freshly downloaded version of Splunk
- You must specify the version of Splunk you used to test (for troubleshooting in case of issues with command deprecation or bugs, etc.)

## Additional Notes
Reference: https://community.splunk.com/t5/Archive/paychex-Splunk-Conf19-Cover-Your-Assets-CYA-Export-error-with/td-p/474803
Note: It is safe to ignore the "Failed to parse templatized search for field" errors for any field originating from the ntags end point, that starts "tagged.*"
