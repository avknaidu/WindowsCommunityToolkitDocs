---
title: RemoteDeviceHelper
author: avknaidu
description: The RemoteDeviceHelper is a Helper to get a List Remote Devices that are accessible.
keywords: windows 10, uwp, windows community toolkit, uwp community toolkit, uwp toolkit, RemoteDeviceHelper, helper
---

# RemoteDevicePicker Control 

The [RemoteDeviceHelper](https://docs.microsoft.com/dotnet/api/microsoft.toolkit.uwp.helpers.remotedevicepicker) gives you a list of Remote Systems. All the systems must be signed in with the same Microsoft Account (MSA)

**Make sure you enable "RemoteSystem" Capability in `package.appxmanifest`**

## Syntax

```c#

RemoteDeviceHelper _remoteDeviceHelper = new RemoteDeviceHelper();

```

You can also use default filer types for initailizing. Like Below.

```c#

var filters = new List<IRemoteSystemFilter>
{
    new RemoteSystemDiscoveryTypeFilter(RemoteSystemDiscoveryType.Cloud),
    new RemoteSystemAuthorizationKindFilter(RemoteSystemAuthorizationKind.SameUser),
    new RemoteSystemStatusTypeFilter(RemoteSystemStatusType.Available)
};

RemoteDeviceHelper _remoteDeviceHelper = new RemoteDeviceHelper(filters);
```

## ## Example

```c#
// without filters

RemoteDeviceHelper _remoteDeviceHelper = new RemoteDeviceHelper();
DevicesList.DataContext = _remoteDeviceHelper;


// with filters

var filters = new List<IRemoteSystemFilter>
{
    new RemoteSystemDiscoveryTypeFilter(RemoteSystemDiscoveryType.Cloud),
    new RemoteSystemAuthorizationKindFilter(RemoteSystemAuthorizationKind.SameUser),
    new RemoteSystemStatusTypeFilter(RemoteSystemStatusType.Available)
};

RemoteDeviceHelper _remoteDeviceHelper = new RemoteDeviceHelper(filters);
DevicesList.DataContext = _remoteDeviceHelper;

```

```xaml

<ListView ItemsSource="{Binding RemoteSystems}" x:Name="DevicesList">
  <ListView.ItemTemplate>
    <DataTemplate>
	  <Grid>
		<Grid.RowDefinitions>
		  <RowDefinition Height="*"/>
		  <RowDefinition Height="*"/>
		</Grid.RowDefinitions>
		<TextBlock Text="{Binding DisplayName}" Tag="{Binding }" Grid.Row="0" />
		<TextBlock Text="{Binding ModelDisplayName}" Tag="{Binding }" Grid.Row="1" />
	  </Grid>
    </DataTemplate>
  </ListView.ItemTemplate>
</ListView>

```

## Sample Code

[RemoteDeviceHelper Sample Page Source](https://github.com/Microsoft/UWPCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.SampleApp/SamplePages/RemoteDeviceHelper). You can see this in action in [Windows Community Toolkit Sample App](https://www.microsoft.com/store/apps/9NBLGGH4TLCQ).

## Requirements

| Device family | Universal, 10.0.16299.0 or higher |
| --- | --- |
| Namespace | Microsoft.Toolkit.Uwp.UI.Controls |
| NuGet package | [Microsoft.Toolkit.Uwp.UI.Controls](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Helpers/) |

## Related Topics

* [Project Rome](https://developer.microsoft.com/en-us/windows/project-rome)
* [Remote Systems Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/RemoteSystems)