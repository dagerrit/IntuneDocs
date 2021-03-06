---
# required metadata

title: Mac OS X policy settings | Microsoft Intune
description: Intune supplies a range of built-in general settings you can configure on Mac OS X devices. Additionally, you can use the Apple Configurator Tool to create custom settings that are not available from Intune.
keywords:
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: heenamac
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Mac OS X configuration policy settings in Microsoft Intune

Intune supplies a range of built-in general settings you can configure on Mac OS X devices. Additionally, you can use the Apple Configurator Tool to create custom settings that are not available from Intune.

## General configuration policy settings

Use the Microsoft Intune **Mac OS X general configuration policy** to configure settings for:

-   **Device security settings** - Choose from a list of predefined settings that let you control a range of features and functionality on the device.

-   **Compliant and noncompliant apps** - Specify a list of apps that are compliant, or not compliant in your company. The Noncompliant Apps Report can be used to view the compliance of apps you specified in the list against the apps that users have installed (but cannot actually block the installation of the app).

If the setting you are looking for does not appear in this list, you might be able to create it using a Mac OS X custom policy that lets you import settings you created using the Apple Configurator Tool. For more information, see **Custom policy settings** later in this topic.

### Password settings

|Setting name|Details|
|----------------|---------------|
|**Require a password to unlock devices**|Specifies whether the use must use a password to access their Mac computer. **Important:** Unlike iOS devices, on Mac OS X devices, the user is not immediately notified to update their password to comply with this setting.|
|**Required password type**|Specifies whether the password used can be Numeric only, or whether it must be **Alphanumeric** (contain letters and numbers). **Important:** This setting is only supported on Mac OS X version 10.10.3 and later.|
|**Number of complex characters required in password**|Specifies the number of complex characters required in the password (from **0** - **4**).<br /><br />A complex character is a symbol, such as '**?**'|
|**Minimum password length**|Specifies the minimum length for the password (between **4** and **14** characters).|
|**Allow simple passwords**|Allows the use of simple passwords such as '**0000**' or '**1234**'.|
|**Minutes of inactivity before password is required**|Specifies how long the computer must be inactive before a password is required to unlock it.|
|**Password expiration (days)**|Specifies how many days elapse before the user must change the password (from **1** - **255** days).|
|**Remember password history**|This setting is used to prevent the user from using a previously used password. When it is set, you can also set **Prevent reuse of previous passwords** to specify the number of previously used passwords that cannot be reused (from **1** - **24**).|
|**Minutes of inactivity before screensaver activates**|Specifies the length of time the computer must be idle before the screensaver activates.|

### Settings for compliant and noncompliant apps
In the **Compliant &amp; Noncompliant Apps list for Mac OS X**, enable **Managed settings for devices**, and then specify a list of compliant or noncompliant apps using the following information:

> [!NOTE]
> A single policy can only contain a list of compliant, or a list of noncompliant apps. You cannot specify both in the same policy.
> 
> Intune lets you report devices with noncompliant apps. It does not block installation, or remove noncompliant apps.

|Setting name|Details|
|----------------|---------------|
|**Report noncompliance when users install the listed apps**|Lists the Mac OS X apps that users are not allowed to install. If users install any of these apps, they will be reported in the **Noncompliant Apps Reports**.|
|**Report noncompliance when users install apps which are not listed**|Lists the Mac OS X apps that users are allowed to install. If users install any other apps, they will be reported in the **Noncompliant Apps Reports**.|
|**Add**|Adds an app to the selected list. Specify a name of your choice, optionally the app publisher, and the  bundle ID of the app. **Tip:** To find the bundle ID of an app, use the following steps on a Mac computer that has the app installed:<ol><li>Open the folder in which the app is installed (for example, **/Applications**)</li><li>Select the *&lt;App Name&gt;***.app** bundle, and choose **Show Package Contents**</li><li>Open the **Info.plist** file</li><li>Check the value associated with the key **CFBundleIdentifier**</li></ol>The format for Bundle ID is **com.contoso.appname**|
|**Import Apps**|Imports a list of apps you have specified in a comma-separated values file. Use the format, app name, publisher, app bundle ID in the file.|
|**Edit**|Let’s you edit the name, publisher and app bundle ID of the selected app.|
|**Delete**|Deletes the selected app from the list.|
> [!TIP]
> For more information about Intune reports, see [Understand Microsoft Intune operations by using reports](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> When a Mac OS X device is in Sleep mode, policies and profiles cannot be delivered or inventoried. As a result, the Intune console might temporarily display the status **Policy settings in error** until the next time the device wakes from Sleep mode.

### Monitor compliant and noncompliant apps
Use the **Noncompliant Apps Reports** to view the compliance of apps you specified.

#### To run the report

1.  In the [Microsoft Intune administration console](https://manage.microsoft.com), click **Reports** &gt; **Noncompliant Apps Reports**.

2.  Select the device groups that you would like to check, whether you want to check for compliant apps, noncompliant apps, or both, then click **View Report**.

## Mac OS X custom policy settings in Microsoft Intune
Use the Microsoft Intune **Mac OS X custom configuration policy** to deploy settings that you created using the [Apple Configurator tool](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) to Mac OS X devices. This tool lets you create many settings that control the operation of these devices and export them to a configuration profile. You can then import this configuration profile into an Intune Mac OS X custom policy and deploy the settings to users and devices in your organization.

This capability is intended to allow you to deploy Mac OS X settings that are not configurable with the Intune Mac OS X general configuration policy.

### Prerequisites
Before you start, you must have installed the Apple Configurator and created a configuration file containing the settings you want to deploy to users or devices. You can download and learn about the Apple Configurator from [the Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

> [!NOTE]
> Intune does not report the compliance of individual settings in a Mac OS X custom policy. However, the overall compliance of the policy is reported.

### General settings

|Setting name|Details|
    |----------------|--------------------|
    |**Name**|Enter a unique name for the Mac OS X custom policy to help you identify it in the Intune console.|
    |**Description**|Provide a description that gives an overview of the Mac OS X custom policy and other relevant information that helps you to locate it.|


### Custom settings

|Setting name|Details|
    |----------------|--------------------|
    |**Custom configuration profile name (displayed to users)**|Provide a name for the policy as it will be displayed on the device, and in Intune policy reports.|
    |**Configuration profile file**|Click **Import**, then browse to the configuration profile that you created using the Apple Configurator. **Tip:** See **How to create a configuration profile file** in this topic for help creating the configuration profile.|
    |**Configuration profile details**|Displays the xml code for the configuration profile that you imported.|



### How to create a configuration profile file
You can create the configuration profile file used by the custom policy in two ways:

-   Export the file (with the extension **.mobileconfig**) from the Apple Configurator tool.

-   Author the file yourself using the appropriate schema from the [Apple Configuration Profile Key Reference](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


> [!IMPORTANT]
> When a Mac OS X device is in Sleep mode, policies and profiles cannot be delivered or inventoried. As a result, the Intune console might temporarily display the status **Policy settings in error** until the next time the device wakes from Sleep mode.

### See also
[Manage settings and features on your devices with Microsoft Intune policies](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

