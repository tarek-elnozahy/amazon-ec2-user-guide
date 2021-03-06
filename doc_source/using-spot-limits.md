# Spot Instance Limits<a name="using-spot-limits"></a>

Spot Instance requests are subject to the following limits:

**Topics**
+ [Spot Request Limits](#spot-limits-general)
+ [Spot Fleet Limits](#spot-fleet-limitations)
+ [T3 Instances](#t3-spot-instances)
+ [T2 Instances](#t2-spot-instances)

## Spot Request Limits<a name="spot-limits-general"></a>

By default, there is an account limit of 20 Spot Instances per region\. If you terminate your Spot Instance but do not cancel the request, the request counts against this limit until Amazon EC2 detects the termination and closes the request\.

Spot Instance limits are dynamic\. When your account is new, your limit might be lower than 20 to start, but increase over time\. In addition, your account might have limits on specific Spot Instance types\. If you submit a Spot Instance request and you receive the error `Max spot instance count exceeded`, you can complete the AWS Support Center [Create Case](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-ec2-spot-instances) form to request an Amazon EC2 instance limit increase\. For **Use Case Description**, indicate that you need an increase in your limits for Spot Instance requests\. For more information, see [Amazon EC2 Service Limits](ec2-resource-limits.md)\.

## Spot Fleet Limits<a name="spot-fleet-limitations"></a>

The usual Amazon EC2 limits apply to instances launched by a Spot Fleet, such as Spot request price limits, instance limits, and volume limits\. In addition, the following limits apply:
+ The number of active Spot Fleets per region: 1,000
+ The number of launch specifications per fleet: 50
+ The size of the user data in a launch specification: 16 KB
+ The target capacity per Spot Fleet: 3,000
+ The target capacity across all Spot Fleets in a region: 5,000
+ A Spot Fleet request can't span regions\.
+ A Spot Fleet request can't span different subnets from the same Availability Zone\.

## T3 Instances<a name="t3-spot-instances"></a>

If you plan to use your T3 Spot Instances immediately and for a short duration, with no idle time for accruing CPU credits, we recommend that you launch your T3 Spot Instances in [`standard`](burstable-performance-instances-standard-mode.md) mode to avoid paying higher costs\.

If you launch your T3 Spot Instances in [`unlimited`](burstable-performance-instances-unlimited-mode.md) mode and burst CPU immediately, you'll spend surplus credits for bursting\. If you use the instance for a short duration, your instance won't have time to accrue CPU credits to pay down the surplus credits, and you'll be charged for the surplus credits when you terminate your instance\.

`Unlimited` mode for T3 Spot Instances is suitable only if the instance runs for long enough to accrue CPU credits for bursting\. Otherwise, paying for surplus credits makes T3 Spot Instances more expensive than M5 or C5 instances\.

## T2 Instances<a name="t2-spot-instances"></a>

Launch credits are meant to provide a productive initial launch experience for T2 instances by providing sufficient compute resources to configure the instance\. Repeated launches of T2 instances to access new launch credits is not permitted\. If you require sustained CPU, you can earn credits \(by idling over some period\), use [T2 Unlimited](burstable-performance-instances-unlimited-mode.md), or use an instance type with dedicated CPU \(for example, `c4.large`\)\.