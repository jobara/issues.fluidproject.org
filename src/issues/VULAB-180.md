---json
{
  "title": "VULAB-180",
  "summary": "Internet Exporer Survey Creation",
  "tags": "VULAB",
  "project": {
    "key": "VULAB",
    "title": "VULab"
  },
  "type": "Bug",
  "priority": "Major",
  "status": "Closed",
  "resolution": "Fixed",
  "assignee": "Blake E",
  "reporter": "Blake E",
  "date": "2009-02-23T13:52:25.000-0500",
  "updated": "2009-03-02T12:21:29.000-0500",
  "versions": [
    "0.5"
  ],
  "fixVersions": [
    "0.5"
  ],
  "components": [
    "Web"
  ],
  "environment": null,
  "issueLinks": [],
  "attachments": [
    {
      "type": "file",
      "url": "https://idrc.cachefly.net/issues.fluidproject.org/VULAB/VULAB-180/VULAB-180.patch",
      "filename": "VULAB-180.patch"
    }
  ],
  "comments": [
    {
      "author": "Blake E",
      "date": "2009-02-23T14:15:16.000-0500",
      "body": "Ha!\n\nOk, so, it wasn't that bad. There is a function which 99% of me believes that it was used for the ajax version of the site.\n\nThe function WAS a jquery one, and I am unsure of why it was not working. I merely commented it out and IE seems to be functioning exactly how it was before.\n\nI'll explain what the function was and why its not being used.\n\nThe Code in Question:\\\npostdata = $('#postdata').text();\\\n//$('#postdata').empty(); //Empty it, its sensitive to stupid people.\\\n//if (postdata) { addLog('harvested postdata!'); addLog(postdata); }\n\nBasically, This code was written as a dirty bridge between php and javascript. It was designed to have php printout some important postdata and then javascript could find it in the DOM, and then it would remove it.\n\nHow was it Used:\\\nIt was used to allow the survey creation process to talk to the javascript. I believe I used this before when I was using the survey tool inline (via ajax) so, when the forum would post it would include the content generated by the survey creation php. This script would grab the postdata generated.\n\nNOTE: after a search through vulab.admin.js there is no other references to postdata so I suspect that it was legacy code - especially so as I did not use the ajax inclusion for vulab.\n\nMy Solution:\\\n1\\. Well, first I opt'd to use iframes which did not require the same javascript awareness in the survey creation process.\n\n2\\. The current system listens for a session variable that is is created when the survey tool is saved in anyway. The session variable (for the survey\\_id) is thrown so php can discover it, and when any button is clicked a javascript event from the iframe reaches up to the parent document to let it know there was a save and the session variable was created.\n"
    },
    {
      "author": "Blake E",
      "date": "2009-02-23T14:21:30.000-0500",
      "body": "vulab17\n"
    }
  ]
}
---
After some testing with JohnC we discovered that internet explorer (unsurprisingly so) breaks.

Specifically during the pre/post survey creation pages within the project editing views.

Where:

* When Editing/Creating Projects
* \- Survey Creation Pages.

The Elements:

* The survey radio buttons to select "new, non, or from existing"

Situation:

* on radio button click, they do not fire off properly to trigger the iframe or other elements that should be included into the page.

        