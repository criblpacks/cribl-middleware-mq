# Middleware Messaging Queue Pack
----

This pack parses messaging queue logs from various vendors, extracting critical key/value pairs based on initial formatting structures.  In addition to cleaning the data to enhance search time performance, non-value add fields or entire info/debug level logs can be dropped to reduce overall ingest volume.

## Requirements

Before you begin, ensure that you have met the following requirements:

**Event Breakers**

IBM MQ logs require event breaking that does not use traditional new line breakers in Syslog messages. If you are sending via TCP, you may be able to configure using the Raw TCP source to add a custom event breaker on ingest.  RabbitMQ and ActiveMQ can use the default Break on Newline.

**IBM MQ Note**

IBMMQ pipeline is using logs formatted from Version 9.0+ 
* Prior to Version 9, the Error Code did not include the letter identifier for log level:
    * I = info
    * W = Warn
    * E = Error
    * S = Severe
* Some Regex Extract functions and Reduction logic will need to be updated if using a version prior to 9

Addition information on Error Codes can be found [here](https://www.ibm.com/docs/en/ibm-mq/9.2?topic=multiplatforms-amq5xxx-installable-services)

## What to Expect

* Easy to read and search Key/Value pairs regardless of original log format
* IBMMQ log reduction of about 20-30% by removing extra characters and spaces
* Ability to remove non-value add fields from all logs before they are sent to SIEM
* Expect greater reduction for all MQ Vendor pipelines if enabling Suppression/Sampling functions

## Using The Pack

To use this Pack, follow these steps:

1. Install the pack
2. Review the Pipelines and triggered functions for the various MQ vendors
2. Ensure your Messaging Queue data source is sending data into LogStream, using appropriate Event Breakers
3. Create a Route for Messaging Queue data and select the cribl_middleware_mq pack as the Pipeline
4. Save a Sample Capture of your own Messaging Queue logs within the Pack to test pipeline functionality on your data


## Release Notes

### Version 0.5 - 2021-07-12
Initial release of the Cribl Middleware MQ pack.
Support for: RabbitMQ, ActiveMQ and IBMMQ (previously IBM Websphere) events

## Contributing to the Pack
Suggest new features or offer to collaborate with us on our Community Slack channel [#packs](https://cribl-community.slack.com/archives/C021UP7ETM3)


## Contact
The author of this pack is Carley Rosato and can be contacted at <carley@cribl.io>


## License
This Pack uses the following license: [`Apache 2.0`](https://github.com/criblio/appscope/blob/master/LICENSE)
