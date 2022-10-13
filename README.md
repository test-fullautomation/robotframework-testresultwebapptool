# RobotResults2DB

[![License: Apache
v2](https://img.shields.io/pypi/l/robotframework.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)

## Table of Contents

-   [Getting Started](#getting-started)
    -   [How to install](#how-to-install)
-   [Usage](#usage)
-   [Example](#example)
-   [Contribution](#contribution)
-   [Sourcecode Documentation](#documentation)
-   [Feedback](#feedback)
-   [About](#about)
    -   [Maintainers](#maintainers)
    -   [Contributors](#contributors)
    -   [License](#license)

## Getting Started

[RobotResults2DB](https://github.com/test-fullautomation/robotframework-testresultwebapptool)
is the tool that helps to import Robot Framework results (**\*.xml**
format) to
[TestResultWebApp](https://github.com/test-fullautomation/TestResultWebApp)
Dashboard.

[RobotResults2DB](https://github.com/test-fullautomation/robotframework-testresultwebapptool)
tool is operating system independent and only works with Python 3.

### How to install

RobotResults2DB is not available on [PyPI](https://pypi.org/) now.

But you can install this package directly from Github repository as
below:

    pip install git+https://github.com/test-fullautomation/robotframework-testresultwebapptool.git

Or you can clone sourcecode to your local directory then install this
package with below steps:

    git clone https://github.com/test-fullautomation/robotframework-testresultwebapptool.git
    cd robotframework-testresultwebapptool
    python setup.py install

After succesful installation, the executable file **RobotResults2DB**
will be available (under *Scripts* folder of Python on Windows and
*\~/.local/bin/* folder on Linux).

In case above location is added to **PATH** environment variable then
you can run it directly as operation system\'s command.

## Usage

[RobotResults2DB](https://github.com/test-fullautomation/robotframework-testresultwebapptool)
tool requires the robot `output.xml` result file(s) and
TestResultWebApp\'s database information for importing.

Try with below command to get tools\'s uage :

    RobotResults2DB -h

The usage should be showed as below: :

    usage: RobotResults2DB (XMLoutput to database importer) [-h] [-v] [-recursive] [-dryrun] [-UUID UUID]
                                                          [--variant VARIANT] [--versions VERSIONS] [--config CONFIG]
                                                          outputfile server user password database

    RobotResults2DB imports XML output files (default: output.xml) generated by the Robot Framework into a WebApp
    database.

    positional arguments:
    outputfile           absolute or relative path to the output file or directory with output files to be imported.
    server               server which hosts the database (IP or URL).
    user                 user for database login.
    password             password for database login.
    database             database schema for database login.

    optional arguments:
    -h, --help           show this help message and exit
    -v                   Version of the RobotResults2DB importer.
    -recursive           if set, then the path is searched recursively for output files to be imported.
    -dryrun              if set, then just show what would be done.
    -UUID UUID           UUID used to identify the import and version ID on webapp. If not provided RobotResults2DB will
                         generate a UUID for the whole import.
    --variant VARIANT    variant name to be set for this import
    --versions VERSIONS  metadata: Versions (Software;Hardware;Test) to be set for this import (semicolon separated).
    --config CONFIG      configuration json file for component mapping information

The below command is simple usage with all required arguments to import
robot results into RQM: :

    RobotResults2DB <outputfile> <server> <user> <password> <database>

Besides the executable file, you can also run tool as a Python module :

    python -m RobotResults2DB <outputfile> <server> <user> <password> <database>

## Example

In order the import the robot result(s) to RQM, we need the `output.xml`
result file.

So, firstly execute the robot testcase(s) to get the `output.xml` result
file.

Sample robot testcase which contains neccessary information for
importing into RQM: :

    *** Settings ***
    # Test execution level
    Metadata   project        ROBFW              # Project/Variant
    Metadata   version_sw     SW_VERSION_0.1     # Software version
    Metadata   version_hw     HW_VERSION_0.1     # Hardware version
    Metadata   version_test   TEST_VERSION_0.1   # Test version

    # File/Suite level
    Documentation             This is description for robot test file
    Metadata    author        Tran Duy Ngoan (RBVH/ECM1)
    Metadata    component     Import_Tools
    Metadata    testtool      Robot Framework 3.2rc2 (Python 3.9.0 on win32)
    Metadata    machine       %{COMPUTERNAME}
    Metadata    tester        %{USER}

    *** Test Cases ***
    Testcase 01
       [Tags]   ISSUE-001   TCID-1001   FID-112   FID-111
       Log       This is Testcase 01

    Testcase 02
       [Tags]   ISSUE-RTC-003   TCID-1002   FID-113
       Log       This is Testcase 01

After getting `output.xml` result file, try with below sample command to
import that result into TestResultWebApp\'s database which is hosted at
*localhost* as below sample command :

    RobotResults2DB output.xml localhost test_user test_pw test_db

Then, open TestResultWebApp with your favourite browser and you will see
how wonderful the execution result is displayed as below figures:

Dashboard view:

![Dashboard view](packagedoc/additional_docs/pictures/Dashboard.png)

Datatable view:

![Datatable view](packagedoc/additional_docs/pictures/Datatable.png)

## Contribution

We are always searching support and you are cordially invited to help to
improve
[RobotResults2DB](https://github.com/test-fullautomation/robotframework-testresultwebapptool)
tool.

## Sourcecode Documentation

To understand more detail about the tool\'s features, parameters and how
Robot testcase information will be displayed on TestResultWebApp, please
refer to [RobotResults2DB tool's
Documentation](https://github.com/test-fullautomation/robotframework-testresultwebapptool/blob/develop/RobotResults2DB/RobotResults2DB.pdf).

## Feedback

Please feel free to give any feedback to us via

Email to: [Robot Framework Support
Group](mailto:RobotFrameworkSupportGroup@bcn.bosch.com)

Issue tracking: [RobotResults2DB
Issues](https://github.com/test-fullautomation/robotframework-testresultwebapptool/issues)

## About

### Maintainers

[Thomas Pollerspöck](mailto:Thomas.Pollerspoeck@de.bosch.com)

[Tran Duy Ngoan](mailto:Ngoan.TranDuy@vn.bosch.com)

### Contributors

[Nguyen Huynh Tri Cuong](mailto:Cuong.NguyenHuynhTri@vn.bosch.com)

[Mai Dinh Nam Son](mailto:Son.MaiDinhNam@vn.bosch.com)

[Tran Hoang Nguyen](mailto:Nguyen.TranHoang@vn.bosch.com)

[Holger Queckenstedt](mailto:Holger.Queckenstedt@de.bosch.com)

### License

Copyright 2020-2022 Robert Bosch GmbH

Licensed under the Apache License, Version 2.0 (the \"License\"); you
may not use this file except in compliance with the License. You may
obtain a copy of the License at

> [![License: Apache
> v2](https://img.shields.io/pypi/l/robotframework.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an \"AS IS\" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
