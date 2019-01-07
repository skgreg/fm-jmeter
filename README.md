# fm-jmeter
Apache JMeter test plan template for FileMaker Server or FileMaker Cloud performance testing.

## fm-jmeter.jmx
This test plan file provides a starting template for performance and load testing for various FileMaker API's, including FileMaker Data API (REST), JDBC, and XML. The template includes the following features:
* User-configurable variables
* Log in to FileMaker Data API to receive an access token. The template uses a single token for all tests.
* Create, edit, and find records via FileMaker Data API requests.
* Create, edit, and find records via JDBC.
* Create, edit, and find records via XML.
* Log out of FileMaker Data API
* See screenshot below for example results. App design, host configuration, and network latency will have a huge impact on the results. These sample results are probably not relevant to your specific environment. Customize the template and test in your own environment! 

## Getting Started
* Install [Apache JMeter](http://jmeter.apache.org). This template was tested with JMeter 4.0. All of the requests work with FileMaker Server 17. The FileMaker Data API tests work with FileMaker Cloud 1.17. 
* Add an account to your test database with fmrest, fmxdbc, and/or fmxml extended privileges. NOTE: The update tests will modify random records, so don't use these tests on a database with real data.
* Open the fm-jmeter.jmx file in JMeter.
* Edit the User Defined Variables page. If you start with the Content Management.fmp12 starter solution, you'll only need to change the server, user, and password variables.
* For JDBC tests, add the fmjdbc.jar driver to the JMeter lib folder.
* Enable/disable thread groups and adjust the number of threads and loop count as appropriate for your environment.
* Customize as needed. Scale up cautiously and only use in dev/testing environments...testing with too many users will crush your server.

## Command Line Testing
While the JMeter GUI is great for setting up and debugging your test plan, it can use a lot of resources. Testing from the command line may give better results. You can test directly on a FileMaker Cloud instance via SSH using a command such as:

~/apache-jmeter-4.0/bin/jmeter -n -t ~/fm-jmeter.jmx -l ~/results.txt -e -o ~/webreport/

## Screenshots

![User Defined Variables](/images/fm-jmeter-variables.png)
![Summary Report](/images/fm-jmeter-summary.gif)
