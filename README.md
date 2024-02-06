# Rerouting EC2 events

This CloudFormation deplyoment is intended to configure AWS EventBridge to re-route all EC2 instance state change events to a custom event bus in N.Virginia (us-east-1).

This event bus will then send all EC2 instance state change events - while applying an [Input Transformer](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-transform-target-input.html) - to an SNS topic in the same region as the event bus.


## File Structure
The [event-propagation-rerouting.yaml](./event-propagation-rerouting.yaml) file should be deployed as [CloudFormation StackSet](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html) in all activated regions.

The [event-propagation-rule.yaml](./event-propagation-rule.yaml) file should be deployed as standalone stack in the N.Virginia region.
