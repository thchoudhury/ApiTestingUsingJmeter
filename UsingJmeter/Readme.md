Downloads JMeter and JMeter plugins and demonstrates usage via examples. 
Suitable for use as a submodule in other projects that contain JMeter Api tests

Dependencies
1. Install JAVA(8+)

Install JMeter and JMeter plugins
1. Downalod Jmeter (http://jmeter.apache.org/download_jmeter.cgi).
2. Download plugins-manager.jar(https://jmeter-plugins.org/get/) and put it into lib/ext directory, then restart JMeter.
3. Install below plugin: a)JSON/YAML Plugins (deprecated)
The installer will also install several JMeter Plugins, which can be used directly or within a continuous integration server such as Jenkins

Open Tests in JMeter
apache-jmeter-5.1.1/bin/jmeter.sh -t tests/my_test.jmx
This will load the JMeter GUI. This very simple test hits https://api.octoperf.com 1 time, with 1 user

Run the tests with Command-R
See results by clicking in any of the Graph or Tree nodes
Stop tests with Command-period
Clear results with Command-E
Running Headless Tests
Especially in a continuous integration server, you'll want to run JMeter tests "headlessly", i.e. without a graphical user interface.

To Run In Non-GUI mode:
apache-jmeter-5.1.1/bin/jmeter.sh -n -t tests/my_test.jmx -l results/my_test.jtl
Let's break this down:

-t tests/my_test.jmx is the test to run
-n results/my_test.jtl tells JMeter to run in non-gui mode
-l provides the path where JMeter will write the test results.

Warning: JMeter logging and results appends
When specifying a log file or .jtl output file, be aware that JMeter appends, not overwrites.

To Generate HTML Report:
apache-jmeter-5.1.1/bin/jmeter.sh -g results/my_test.jtl -o reports/my_test_report

All test result and graph details can be found in reports/my_test_report/index.html.

