# RobotFramework UV Test

Universal Content Viewer:
Here is an introduction to the automation suite for the Universal Content Viewer project. There will be an attached requirement sheet that you will need in order for you to run tests and to be able to setup the right python environment. It is recommended to use a virtual environment with a base python of v4 (Which is what it has been tested on).

In the Test directory we have 13 suites in total that are there to ensure that once the project has started will cover each granular tests from API to Geo-locking and permissions. All web tests can be run on chrome and edge (Currently having issues with FireFox). Browsers, Environments and locations etc. can be found within the "Input_Data" robot keyword file, these can be changed to ensure we have full versatility over our data in the suite.

Tests: 01__Regression.robot
There's multiple tests within this suite that all to handle the various features in Universal content viewer, all tests in this suite has the same Tag , which is stated in the command below. 

To run this test we type the following into the Terminal, >python -m robot -d Results -i 01__Regression1 tests/01__Regression.robot 

For loop from arks within spreadsheet (sounds only):

In the first test, this is a for loop test that allows a tester to run through around 40 different Arks and applies then to the Base URL (Environment) there's two ways we can change the Base URL in the suite, however in the first test all we need to do to change this is by changing the base URL inside the Input data file. The second way is helped by the dialog library, in which allows the tester to switch the base URL for each ARK within the spreadsheet by a dialog selector that appears when running the test, this will be explained later on in this document.

Loop-Sound-ARK's.mp4

Looping arks

The run multiple sounds test is nested into 3 different directories, the KeywordsApp and the ARK's keyword file. The ARK's keyword file contains the logic for the for loops which also can apply for different ark type's such as, Manuscripts and Books but as we have limited data for those two items, sounds seemed like a perfect start and is relevant to the ongoing project.

https://wiki.bl.uk:8443/download/attachments/253199305/Loop-Sound-ARK%27s.mp4?version=1&modificationDate=1626182814663&api=v2

Adding different item Ark's to environment:

In continuation to the adding Ark's to environments, the next test is to apply all 3 items to an environment and wait for them to display fully. Again like the last test this uses the KeywordApp and another keyword file called LandingPage, It's a relatively simple test although this is a good test to see how the UI (View controller/wrapper) reacts to different items being applied to the environment.

https://wiki.bl.uk:8443/download/attachments/253199305/Different-Items.mp4?version=1&modificationDate=1626183286500&api=v2

Navigating Item and pages:

Opening Universal Viewer test is to mimic the users integrations with the item by zooming and navigation around the item that's within the Book and Manuscript arks, this test is currently only for the Book arks but can be easily modified to use the Manuscript items.

https://wiki.bl.uk:8443/download/attachments/253199305/UI-Test.mp4?version=1&modificationDate=1626183606080&api=v2

This also ties in nicely with the fourth test which is, Navigating universal viewer again this test is to mimic a users interacting with the elements inside the wrapper of the universal content viewer. It's important to note that this test only applies to the Book Arks, as this uses the pages to navigate through each page and tests the bounds within this, these set of tests are important for the look and feel of the Universal Content Viewer. 

Verifying Diacritics for multiple ark types:

Locale (translate) eng (gb) to All is a set of tests that will open any Ark type and will navigate the user to the settings and change the language. This works by verifying after the page has refreshed the diacritics that are displayed within the information and checking that they've appeared. At the moment this only verifies the cancel button on the settings dialog, it will need changing once we have relevant arks in place for the test.

https://wiki.bl.uk:8443/download/attachments/253199305/Diacritics.mp4?version=1&modificationDate=1626183876749&api=v2

Geo-locking and rights:

Setting geolocation for rights based testing, as the title of this test implies we have to set the geolocation from a data_input keyword file which contains the longitude and latitude of each country in a list. This allows the user to mimics opening multiple ark types from a different region/country. In the test itself sets the location then opens an ARK and can be applied to all other ARK types relatively easily. We can check this has worked as expected by looking within the log file from our RobotFramework suite. This is a powerful test as we can also apply this to cover all RAQ ID's permissions that requires certain items be restricted by geo-locking.

https://wiki.bl.uk:8443/download/attachments/253199305/Geo-Location-Rights.mp4?version=1&modificationDate=1626181277970&api=v2

Dialog Test Cases: 

The first test case from the dialog tests, allows the tester to apply different items to the environment and can check how the wrapper/view controller handles these changes. The reason why there's dialog test cases is to keep the data_input file organized and to allow the tester to change data when running scripts without changing anything in the data keyword file. As mentioned in the for loop section, we can use the dialog library to switch the base URL for each ARK within the spreadsheet containing multiple sound ARK's by a dialog selector that appears when running the test. The benefit of this is when the developer decides to merge changes across environments we can quickly change the ENV from the picker and run scripts to accommodate to the change in the environment without manually changing data within our suite.  This can be applied across all environments efficiently with the dialog picker, the video below demonstrates how we can do this. 

https://wiki.bl.uk:8443/download/attachments/253199305/Dialog-ENV.mp4?version=1&modificationDate=1626184081239&api=v2

Multiple Browser Testing

The multiple Browser test, this test I found particularly useful as it tests across all key browsers all at once rather than changing the data_input file to change the browser which definitely saves us time. We can do this by the following. We use a for loop which will use the browser list that's inside the data_input file, in with we call {i} which will call each browser separately after its run through one browser from @{browser_list} variable.

https://wiki.bl.uk:8443/download/attachments/253199305/All%20browser%20loop.mp4?version=1&modificationDate=1626180133440&api=v2

UV__API :

For the API automation is a key part of my suite, this will allow us to test the rights and specific RAQ-ID requirements which may include geolocation or displaying specific content to certain users. I have managed to include authentication in my tests which will allow me to use different users/role credentials, this is spread across all of the key environments use for development. This easily changeable and to edit as mentioned multiple times from the data_input file which holds every RAQ-ID required for the business needs, all environment data and lists to make it easily to create scripts from.

https://wiki.bl.uk:8443/download/attachments/253199305/API%20Test.mp4?version=1&modificationDate=1626179855884&api=v2

Save these spreadsheets to get your tests running:
https://bluk-my.sharepoint.com/:x:/g/personal/danny_taylor_bl_uk/EYwHz7D4IIFAhdvcqdbhpfoBKUZoXPO6oDLbtoCc2VvXlw
https://bluk-my.sharepoint.com/:x:/g/personal/danny_taylor_bl_uk/Eeiibgy4H4xOjna3dXDhwncBAuYyGlAnQHVbYyNCVRIJBA
https://bluk-my.sharepoint.com/:x:/g/personal/danny_taylor_bl_uk/Ef23rO_CGD5OmXtmyv3M4lwB-NNF0xMrtcmg3F_nKitmZQ
https://bluk-my.sharepoint.com/:x:/g/personal/danny_taylor_bl_uk/EeJ1_Z5XI2xLpSF3A54f4oEBKHjCNEv31vSvzWMtc6w5kA