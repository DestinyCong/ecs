# DescribeImages

You can call this operation to query available images.

## Description

-   You can query your custom images, public images provided by Alibaba Cloud, Alibaba Cloud Marketplace images, and shared images from other Alibaba Cloud accounts.
-   This operation supports paged query. The response contains the total number of available images and the images on the returned page. By default, ten entries are displayed on each page.
-   When you call an API operation by using Alibaba Cloud Command Line Interface \(CLI\), you must specify request parameter values of different data types in required formats. For more information, see [CLI parameter format](~~110340~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=DescribeImages&type=RPC&version=2014-05-26)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeImages|The operation that you want to perform. Set the value to DescribeImages. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the images to be queried. You can call the [DescribeRegions](~~25609~~) operation to query the most recent region list. |
|Status|String|No|Available|The status of the image. Default value: Available. Valid values:

-   Creating: The image is being created.
-   Waiting: The image is waiting to be processed.
-   Available: The image is available.
-   UnAvailable: The image is unavailable.
-   CreateFailed: The image failed to be created.
-   Deprecated: The image is discontinued.

Separate multiple parameter values with commas \(,\). |
|ImageId|String|No|m-bp1g7004ksh0oeuc\*\*\*\*|The ID of the image. |
|ShowExpired|Boolean|No|false|Specifies whether the subscription image has expired.

**Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure future compatibility. |
|SnapshotId|String|No|s-bp17ot2q7x72ggtw\*\*\*\*|The ID of the snapshot used to create the custom image. |
|ImageName|String|No|testImageName|The name of the image. |
|ImageFamily|String|No|hangzhou-daily-update|The name of the image family. You can set this parameter to query images of the specified image family.

This parameter is empty by default. |
|ImageOwnerAlias|String|No|self|The source of the image. Valid values:

-   system: public images provided by Alibaba Cloud.
-   self: your custom images.
-   others: shared images from other Alibaba Cloud accounts.
-   marketplace: Alibaba Cloud Marketplace images. If Alibaba Cloud Marketplace images are returned in the response, you can use the images without subscription. You must pay attention to the billing details of Alibaba Cloud Marketplace images.

This parameter is empty by default, which indicates that the results that match system, self, and others are returned. |
|InstanceType|String|No|ecs.g5.large|The instance type for which the image can be used. |
|IsSupportIoOptimized|Boolean|No|true|Specifies whether the image can be used on I/O optimized instances. |
|IsSupportCloudinit|Boolean|No|true|Specifies whether the image supports cloud-init. |
|OSType|String|No|linux|The operating system type of the image. Valid values:

-   windows
-   linux |
|Architecture|String|No|i386|The image architecture. Valid values:

-   i386
-   x86\_64 |
|PageNumber|Integer|No|1|The number of the page to return. Pages start from page 1.

Default value: 1. |
|PageSize|Integer|No|1|The number of entries to return on each page. Valid values: 1 to 100.

Default value: 10. |
|Usage|String|No|instance|Specifies whether the image is running on an ECS instance. Valid values:

-   instance: The image is already in use and running on an ECS instance.
-   none: The image is not in use. |
|Tag.N.value|String|No|null|The value of tag N of the image.

**Note:** This parameter will be removed in the future. We recommend that you use the Tag.N.Value parameter to ensure future compatibility. |
|Tag.N.key|String|No|null|The key of tag N of the image.

**Note:** This parameter will be removed in the future. We recommend that you use the Tag.N.Key parameter to ensure future compatibility. |
|Tag.N.Key|String|No|TestKey|The key of tag N of the image. Valid values of N: 1 to 20.

If you query resources by using a single tag, up to 1,000 resources with the tag can be returned. If you query resources by using multiple tags, up to 1,000 resources that have the tags attached can be returned. If you want to query information of more than 1,000 resources, use the [ListTagResources](~~110425~~) operation. |
|Tag.N.Value|String|No|TestValue|The value of tag N of the image. Valid values of N: 1 to 20. |
|DryRun|Boolean|No|false|Specifies whether to check the validity of the request without actually making the request.

-   true: The validity of the request is checked but resources are not queried. Check items include whether your AccessKey pair is valid, whether RAM users are authorized, and whether the required parameters are specified. If the check fails, the corresponding error message is returned. If the check succeeds, the DryRunOperation error code is returned.
-   false: The validity of the request is checked, and a 2XX HTTP status code is returned and resources are queried if the check succeeds.

Default value: false. |
|ActionType|String|No|CreateEcs|The scenario in which the image is used. Default value: CreateEcs. Valid values:

-   CreateEcs: instance creation
-   ChangeOS: replacement of the system disk or operating system |
|Filter.N.Key|String|No|CreationStartTime|The key of filter N. |
|Filter.N.Value|String|No|2017-12-05T22:40:00Z|The value of filter N. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4p\*\*\*\*|The ID of the resource group to which the custom image belongs. Up to 1,000 resources can be returned by a query based on this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Images|Array of Image| |The collection of information about images. |
|Image| | | |
|Architecture|String|x86\_64|The image architecture. Valid values:

-   i386
-   x86\_64 |
|CreationTime|String|2018-01-10T01:01:10Z|The time when the image was created. |
|Description|String|Archive log for Oracle|The description of the image. |
|DiskDeviceMappings|Array of DiskDeviceMapping| |The mappings between disks and snapshots under the image. |
|DiskDeviceMapping| | | |
|Device|String|/dev/xvdb|The device name of the disk. Example: /dev/xvdb.

**Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure future compatibility. |
|Format|String|qcow2|The format of the image. |
|ImportOSSBucket|String|testEcsImport|The OSS bucket that contains the imported image file. |
|ImportOSSObject|String|imageImport|The OSS object that corresponds to the imported image file. |
|Progress|String|32%|The progress of an image copy task. |
|RemainTime|Integer|213|The remaining time for an image copy task. Unit: seconds. |
|Size|String|80|The size of the disk. |
|SnapshotId|String|s-bp17ot2q7x72ggtw\*\*\*\*|The ID of the snapshot. |
|Type|String|custom|The type of the image. |
|ImageFamily|String|as-hangzhou-game-01|The name of the image family. |
|ImageId|String|m-bp1g7004ksh0oeuc\*\*\*\*|The ID of the image. |
|ImageName|String|testImageName|The name of the image. |
|ImageOwnerAlias|String|self|The alias of the image owner. Valid values:

-   system: public images provided by Alibaba Cloud
-   self: your custom images
-   others: shared images from other Alibaba Cloud accounts
-   marketplace: Alibaba Cloud Marketplace images |
|ImageVersion|String|2|The version of the image. |
|IsCopied|Boolean|false|Indicates whether the image is a copy of another image. |
|IsSelfShared|String|true|Indicates whether the image has been shared to other Alibaba Cloud accounts. |
|IsSubscribed|Boolean|false|Indicates whether you have subscribed to the image that corresponds to the specified product code. |
|IsSupportCloudinit|Boolean|true|Indicates whether the image supports cloud-init. |
|IsSupportIoOptimized|Boolean|true|Indicates whether the image can be used on I/O optimized instances. |
|OSName|String|Alibaba Cloud Linux 2.1903|The Chinese name of the operating system. |
|OSNameEn|String|Alibaba Cloud Linux 2.1903|The English name of the operating system. |
|OSType|String|Linux|The type of the operating system. Valid values:

-   windows
-   linux |
|Platform|String|Aliyun|The platform of the operating system. |
|ProductCode|String|jxsc000204|The product code of the Alibaba Cloud Marketplace image. |
|Progress|String|100|The image creation progress. Unit: percent \(%\). |
|ResourceGroupId|String|rg-bp67acfmxazb4p\*\*\*\*|The ID of the resource group to which the image belongs. |
|Size|Integer|80|The size of the image. Unit: GiB. |
|Status|String|Available|The status of the image. Valid values:

-   UnAvailable: The image is unavailable.
-   Available: The image is available.
-   Creating: The image is being created.
-   CreateFailed: The image failed to be created. |
|Tags|Array of Tag| |An array of tag pairs of the image. |
|Tag| | | |
|TagKey|String|TestKey|The tag key of the image. |
|TagValue|String|TestValue|The tag value of the image. |
|Usage|String|none|Indicates whether the image has been used to create ECS instances. Valid values:

-   instance: The image has been used to create one or more ECS instances.
-   none: The image has not been used to create ECS instances. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|1|The number of entries returned per page. |
|RegionId|String|cn-hangzhou|The region ID of the image. |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |
|TotalCount|Integer|24|The total number of images. |

## Examples

Sample requests

```
https://ecs.aliyuncs.com/?Action=DescribeImages
&RegionId=cn-hangzhou
&PageSize=1
&PageNumber=1
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeImagesResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>61</TotalCount>
      <PageSize>1</PageSize>
      <RegionId>cn-hangzhou</RegionId>
      <RequestId>66189103-EDB2-43E2-BB60-BFF2B62F4EB8</RequestId>
      <Images>
            <Image>
                  <ImageId>m-bp1g7004ksh0oeuc****</ImageId>
                  <ImageFamily>hangzhou-daily-update</ImageFamily>
                  <Description>Archive log for Oracle</Description>
                  <OSNameEn>Windows Server  2016 Data Center Edition 64bit Chinese Edition</OSNameEn>
                  <ProductCode></ProductCode>
                  <ResourceGroupId></ResourceGroupId>
                  <OSType>windows</OSType>
                  <Architecture>x86_64</Architecture>
                  <OSName>Windows Server 2016 Datacenter Edition 64-bit (Chinese)</OSName>
                  <DiskDeviceMappings>
                        <DiskDeviceMapping>
                              <ImportOSSObject></ImportOSSObject>
                              <Format></Format>
                              <Device>/dev/xvda</Device>
                              <Type>system</Type>
                              <SnapshotId>s-bp17ot2q7x72ggtw****</SnapshotId>
                              <ImportOSSBucket></ImportOSSBucket>
                              <Progress></Progress>
                              <Size>60</Size>
                        </DiskDeviceMapping>
                  </DiskDeviceMappings>
                  <ImageOwnerAlias>self</ImageOwnerAlias>
                  <Progress>100%</Progress>
                  <IsSupportCloudinit>true</IsSupportCloudinit>
                  <Usage>none</Usage>
                  <CreationTime>2019-11-15T06:07:05Z</CreationTime>
                  <ImageVersion></ImageVersion>
                  <Tags>
                        <Tag>
                              <TagValue>Oracle</TagValue>
                              <TagKey>DTS</TagKey>
                        </Tag>
                  </Tags>
                  <Status>Available</Status>
                  <ImageName>Oracle_DTS</ImageName>
                  <IsSupportIoOptimized>true</IsSupportIoOptimized>
                  <IsSelfShared>False</IsSelfShared>
                  <IsCopied>false</IsCopied>
                  <IsSubscribed>false</IsSubscribed>
                  <Platform>Windows Server 2016</Platform>
                  <Size>60</Size>
            </Image>
      </Images>
</DescribeImagesResponse>
```

`JSON` format

```
{
    "PageNumber": 1,
    "TotalCount": 61,
    "PageSize": 1,
    "RegionId": "cn-hangzhou",
    "RequestId": "66189103-EDB2-43E2-BB60-BFF2B62F4EB8",
    "Images": {
        "Image": [
            {
                "ImageId": "m-bp1g7004ksh0oeuc****",
                "ImageFamily": "hangzhou-daily-update",
                "Description": "Archive log for Oracle",
                "OSNameEn": "Windows Server  2016 Data Center Edition 64bit Chinese Edition",
                "ProductCode": "",
                "ResourceGroupId": "",
                "OSType": "windows",
                "Architecture": "x86_64",
                "OSName": "Windows Server 2016 Datacenter Edition 64-bit (Chinese)",
                "DiskDeviceMappings": {
                    "DiskDeviceMapping": [
                        {
                            "ImportOSSObject": "",
                            "Format": "",
                            "Device": "/dev/xvda",
                            "Type": "system",
                            "SnapshotId": "s-bp17ot2q7x72ggtw****",
                            "ImportOSSBucket": "",
                            "Progress": "",
                            "Size": "60"
                        }
                    ]
                },
                "ImageOwnerAlias": "self",
                "Progress": "100%",
                "IsSupportCloudinit": true,
                "Usage": "none",
                "CreationTime": "2019-11-15T06:07:05Z",
                "ImageVersion": "",
                "Tags": {
                    "Tag": [
                        {
                            "TagValue": "Oracle",
                            "TagKey": "DTS"
                        }
                    ]
                },
                "Status": "Available",
                "ImageName": "Oracle_DTS",
                "IsSupportIoOptimized": true,
                "IsSelfShared": "False",
                "IsCopied": false,
                "IsSubscribed": false,
                "Platform": "Windows Server 2016",
                "Size": 60
            }
        ]
    }
}
```

## Error codes

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidImageOwnerAlias.ValueNotSupported|The specified ImageOwnerAlias value is not supported.|The error message returned because the specified value of the ImageOwnerAlias parameter is invalid.|
|400|InvalidParamter|Invalid Parameter|The error message returned because a specified parameter is invalid.|
|404|InvalidFilterKey.NotFound| |The error message returned because the specified start time or end time is invalid.|
|404|InvalidUsage|The specifed Usage is not valid|The error message returned because the specified Usage parameter is invalid.|
|400|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|The error message returned because the specified Tag.N.Key and Tag.N.Value parameters do not match.|
|400|InvalidTagCount|The specified tags are beyond the permitted range.|The error message returned because the number of specified tags has exceeded the upper limit.|
|400|InvalidInstanceType.ValueNotSupported|The specified InstanceType does not exist or beyond the permitted range.|The error message returned because the specified instance type does not exist or you are not authorized to manage instances of this instance type.|
|404|InvalidOSType|The specifed OSType is not valid|The error message returned because the specified operating system is not supported.|
|404|InvalidArchitecture|The specifed Architecture is not valid|The error message returned because the specified Architecture parameter does not exist.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

