---json
{
  "title": "FLUID-2380",
  "summary": "jQuery UI dialog, should be styled using FSS",
  "tags": "FLUID",
  "project": {
    "key": "FLUID",
    "title": "Fluid Infusion"
  },
  "type": "Bug",
  "priority": "Critical",
  "status": "Closed",
  "resolution": "Fixed",
  "assignee": "Jacob Farber",
  "reporter": "Justin Obara",
  "date": "2009-03-18T14:22:59.000-0400",
  "updated": "2011-02-28T16:45:19.139-0500",
  "versions": [
    "1.0"
  ],
  "fixVersions": [
    "1.1"
  ],
  "components": [
    "UI Options"
  ],
  "environment": "FF2, FF3, Opera 9.6, Safari 3.2 (Mac OS 10.5)\\\nSafari 3.2 (Mac OS 10.4)\\\nFF2, FF3, IE6, IE7, Opera 9.6 (Win XP)\\\nFF3, IE7 (Win Vista)\\\nIE6 (Win 2000)\n",
  "issueLinks": [
    {
      "type": "Related to",
      "url": "/browse/FLUID-2388/",
      "key": "FLUID-2388",
      "summary": "The UI Options dialog does not have a default background colour that is not dependend on the entire site using an FSS theme"
    }
  ],
  "attachments": [],
  "comments": [
    {
      "author": "Justin Obara",
      "date": "2009-03-18T15:54:56.000-0400",
      "body": "Bug Parade release comment removed\n"
    },
    {
      "author": "Anastasia Cheetham",
      "date": "2009-03-23T15:37:50.000-0400",
      "body": "I've reviewed the changes for this fix. They look good, but there are some commented lines in the sakai.html header and in the sakai.js dialog\\_container.dialog() initialization that should be removed.\n"
    },
    {
      "author": "Justin Obara",
      "date": "2009-03-23T15:39:37.000-0400",
      "body": "need to removed commented out code\n"
    },
    {
      "author": "Anastasia Cheetham",
      "date": "2009-03-23T16:39:45.000-0400",
      "body": "Looks good +1\n"
    },
    {
      "author": "Justin Obara",
      "date": "2009-03-23T17:22:22.000-0400",
      "body": "Verified fix using:\n\nFF2, FF3, Opera 9.6, Safari 3.2 (Mac OS 10.5)\\\nFF2, FF3, IE6, Opera 9.6 (Win XP)\\\nFF3, IE7 (Win Vista)\n"
    },
    {
      "author": "Justin Obara",
      "date": "2009-03-24T10:27:33.000-0400",
      "body": "use custom jQuery UI Themes for jQuery UI widgets\n"
    },
    {
      "author": "Michelle D'Souza",
      "date": "2009-03-26T11:30:01.000-0400",
      "body": "There have been improvements made for 1.0 but there are still more improvements to be made.\n"
    },
    {
      "author": "Justin Obara",
      "date": "2009-05-14T09:06:41.000-0400",
      "body": "Bug Parade 1.1 release\n"
    },
    {
      "author": "Laurel Williams",
      "date": "2009-05-25T14:56:41.000-0400",
      "body": "Had a look at the code changes, which are quite extensive and touch many files. \\*note some of the file names seem to have changed since these file names were generated by commit emails. Did not see anything which caused offense. Visually checked these out in Opera, IE8, FF3 on win xp.\n\nM /fluid/components/trunk/src/webapp/fluid-components/css/fluid.layout.css\\\nM /fluid/components/trunk/src/webapp/fluid-components/css/fluid.theme.coal.css\\\nM /fluid/components/trunk/src/webapp/fluid-components/css/fluid.theme.mist.css\\\nM /fluid/components/trunk/src/webapp/fluid-components/css/fluid.theme.slate.css\\\nM /fluid/components/trunk/src/webapp/sample-code/shared/sakai/css/sakai.css\\\nM /fluid/components/trunk/src/webapp/sample-code/shared/sakai/js/sakai.js\\\nM /fluid/components/trunk/src/webapp/sample-code/shared/sakai/sakai.html\\\nM /fluid/infusion/trunk/src/webapp/integration-demos/sakai/html/ui-options-fss-sakai.html\\\nM /fluid/infusion/trunk/src/webapp/components/uiOptions/css/UIOptions.css\\\nM /fluid/infusion/trunk/src/webapp/components/uiOptions/html/UIOptions.html\\\nM /fluid/infusion/trunk/src/webapp/lib/jquery/ui/css/fl-theme-coal/jquery-ui-1.7.1.custom.css\\\nM /fluid/infusion/trunk/src/webapp/lib/jquery/ui/css/fl-theme-hc/jquery-ui-1.7.1.custom.css\\\nM /fluid/infusion/trunk/src/webapp/lib/jquery/ui/css/fl-theme-hci/jquery-ui-1.7.1.custom.css\\\nM /fluid/infusion/trunk/src/webapp/lib/jquery/ui/css/fl-theme-mist/jquery-ui-1.7.1.custom.css\\\nM /fluid/infusion/trunk/src/webapp/lib/jquery/ui/css/fl-theme-slate/jquery-ui-1.7.1.custom.css\\\n\\+ numerous images\n"
    },
    {
      "author": "Justin Obara",
      "date": "2009-05-25T15:50:05.000-0400",
      "body": "Needs to update file names for css files and fix broken images\n"
    },
    {
      "author": "Jacob Farber",
      "date": "2009-05-25T16:09:51.000-0400",
      "body": "Inverted high contrast theme has broken images, so i will re-download the theme\n"
    },
    {
      "author": "Michelle D'Souza",
      "date": "2011-02-28T16:45:19.137-0500",
      "body": "Closing issues that were fixed in 1.1\n"
    }
  ]
}
---
jQuery UI dialog, should be styled using FSS

Currently the jQuery UI Dialog is using it's own styles, instead of the FSS styles set in UI Options.

Steps to reproduce:

1\) Open the sakai mock-up example from the daily build site\
<http://build.fluidproject.org/fluid/sample-code/shared/sakai/sakai.html>

2\) Open the UI Options dialog

3\) Change some of the options, and save the changes.

Notice that the dialog doesn't change

        