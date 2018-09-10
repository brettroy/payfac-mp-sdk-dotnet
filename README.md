[![Build Status](https://travis-ci.org/Vantiv/payfac-mp-sdk-dotnet.svg?branch=13.x)](https://travis-ci.org/Vantiv/payfac-mp-sdk-dotnet)
![Github All Releases](https://img.shields.io/github/downloads/vantiv/payfac-mp-sdk-java/total.svg)
[![GitHub](https://img.shields.io/github/license/vantiv/payfac-mp-sdk-java.svg)](https://github.com/Vantiv/payfac-mp-sdk-java/13.x/LICENSE) [![GitHub issues](https://img.shields.io/github/issues/vantiv/payfac-mp-sdk-java.svg)](https://github.com/Vantiv/payfac-mp-sdk-java/issues)

# payfac-mp-sdk-dotnet

The PayFac Merchant Provisioner SDK is a C# implementation of the [Worldpay](https://developer.vantiv.com/community/ecommerce) PayFac Merchant Provisioner API. This SDK was created to make it as easy as possible to perform operations that allows you to create and update Legal Entities and Sub-merchants, as well as retrieve information about existing Legal Entities and Sub-merchants in near real-time. This SDK utilizes the HTTPS protocol to securely connect to Worldpay. Using the SDK requires coordination with the Vantiv eCommerce team in order to be provided with credentials for accessing our systems.

Each .NET SDK release supports all of the functionality present in the associated PayFac Merchant Provisioner API version (e.g., SDK v13.0.0 supports API v13.0.0). Please see our [documentation](https://developer.vantiv.com/community/ecommerce/pages/documentation) for PayFac Merchant Provisioner API to get more details on what operations are supported.

This SDK is implemented to support the .NET plaform, including C#, VB.NET and Managed C++ and is created by Worldpay. Its intended use is for PayFac API operations with Worldpay.

## Getting Started

These instructions will help you get started with using the SDK.

### Prerequisites

None.

### Setup

1.) To install it, copy PayFacSdkForNet.dll into your Visual Studio references.

2.) You can configure it statically by adding the following section to your project's App.config
```
    <configSections>
        <sectionGroup name="vantivEcommerce">
            <section name="chargebackSettings"
                     type="System.Configuration.NameValueSectionHandler" />
        </sectionGroup>
    </configSections>
    <vantivEcommerce>
        <chargebackSettings>
            <add key="username" value="myUsername" />
            <add key="password" value="myPassword" />
            <add key="merchantId" value="777777" />
            <add key="host" value="https://www.testvantivcnp.com/sandbox/new/services" />
            <add key="printXml" value="true" />
            <add key="proxyHost" value="myProxyHost" />
            <add key="proxyPort" value="7777" />
            <add key="neuterXml" value="false" />
        </chargebackSettings>
    </vantivEcommerce>
```
Also, you can use a different Configuration constructor to pass a file path to a simple configuration file that contains [key=value] settings; an example of this configuration file can be found at (https://github.com/Vantiv/cnp-chargeback-sdk-dotNet/blob/2.x/sampleConfig.txt). 
```
    username = myUsername
    password = myPassword
    merchantId = 777777
    host = https://www.testvantivcnp.com/sandbox/new/services
    printXml = true
    neuterXml = false
    proxyHost = myProxyHost
    proxyPort = 7777
```
In addition, you can configure it dynamically by create a dictionary with required settings and call the Configuration constructor taking a dictionary.


### Configuration
List of configuration parameters along with their values can be found [here](https://gist.github.com/VantivSDK/8b7dd606230ec65b36eba457df4443de).

## Usage example

Let's try our SDK with the Sandbox, which doesn't require a valid username and password:  

```c#
using System;
using ChargebackSdkForNet;

namespace Merchant
{
    internal class Program
    {
        public static void Main(string[] args)
        {
            var request = new ChargebackRetrievalRequest();
            request.Config.Set("host", "https://www.testvantivcnp.com/sandbox/new/services");
            var dateTime = new DateTime(2013,1,1);
            var response = request.RetrieveByActivityDate(dateTime);
            var cases = response.chargebackCase;
            foreach (var c in cases)
            {
                Console.WriteLine("Case Id:" + c.caseId);
            }
        }
    }
}
```

Compile and run this file.  You should see the following result:
~~~
    Case Id:1288791001
~~~

## Versioning
For the versions available, see the [tags on this repository](https://github.com/vantiv/payfac-mp-sdk-java/tags). 

## Changelog
For the list of changes, check out the [changelog](https://github.com/Vantiv/payfac-mp-sdk-java/blob/13.x/CHANGELOG.md)

## Authors

* [**Charmik Sheth**](https://github.com/Charmik-Sheth)
* [**Kartik Dave**](https://github.com/davekartik24)

See also the list of [contributors](https://github.com/vantiv/payfac-mp-sdk-java/contributors) who participated in this project.

## License
This project is licensed under the MIT License - see the [LICENSE](https://github.com/Vantiv/payfac-mp-sdk-java/blob/13.x/LICENSE.md) file for details

## Examples
More examples can be found in [Functional and Unit Tests](https://github.com/Vantiv/payfac-mp-sdk-dotnet/tree/13.x/src/test/java/com/mp/sdk)

## Support
Please contact [Vantiv eCommerce](https://developer.vantiv.com/community/ecommerce) to receive valid merchant credentials in order to run tests successfully or if you require assistance in any way.  Support can also be reached at sdksupport@Vantiv.com
