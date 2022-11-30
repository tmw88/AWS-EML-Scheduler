# AWS-EML-Scheduler
## About
AWS-EML-Scheduler is a tool that automates the process of input switching and scheduling livestream broadcasts in AWS Elemental Media Live using AWS API. A list of all current encoders stored in the cloud is generated upon running, along with the corresponding video attachments and ID for each encoder.
## Usage
Refer to generated list to see attached video inputs and ID.


Two options are presented: 
- type: `scte` for SCTE-35 Time Signal
- type: `input` for Input Switch

## `scte` Option
- Enter `ID` for channel
- Enter a name for the action being created
- Enter `SegmentationUpid`
> `SegmentationUpid` must be hexadecimal and must contain an even amount of hex characters.
- Enter `SegmentationTypeId`
> Refer to [https://wagtail-prod-storage.s3.amazonaws.com/documents/SCTE_35_2022.pdf] pages 66-68 to find decimal ID's of corresponding segmentation messages.
- Enter `startType`: `fixed` or `follow`
> For `fixed` start type, Format: 0000-00-00T00:00:00.000Z 
>> e.g. 2022-08-21T09:30:00.000Z 
>>> in order of YEAR, MONTH, DAY, HOUR, MINUTE, SECOND.
##
> For `follow` start type, enter the name of the input that will precede the new SCTE-35 message.
>> SCTE-35 messages must follow an active input. If encoder has no active inputs, new message will not be created.
## `input` Option
- Enter `ID` for channel
- Enter a name for the action being created
- Enter the input name you want attached
> List of input names are shown for each encoder in the generated list
- Enter `startType`: `fixed`, `follow`, or `immediate`
> For `fixed` start type, Format: 0000-00-00T00:00:00.000Z
>> e.g. 2022-08-21T09:30:00.000Z 
>>> in order of YEAR, MONTH, DAY, HOUR, MINUTE, SECOND.
##
> For `follow` start type, enter the name of the input that will precede the new input switch.
>> Must follow an active input. If encoder has no active inputs, new input will not be created.
##
> For `immediate` start type, input will immediately start. This will replace the current input if one is active at the time of deployment.
