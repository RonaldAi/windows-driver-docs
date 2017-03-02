---
Description: 'USBStress is the combination of a user-mode application (usbstress.exe) and driver installation package for the kernel-mode driver, usbstress.sys.'
MS-HAID: 'buses.usbstress'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
title: USBStress
---

# USBStress


USBStress is the combination of a user-mode application (usbstress.exe) and driver installation package for the kernel-mode driver, usbstress.sys.

Those files are included in the [MUTT Software Package](http://msdn.microsoft.com/windows/hardware/jj590752).

## USBStress


USBStress is a set of tests focused on the entire USB driver stack and the USB Generic Parent Driver (Usbccgp.sys), and controller and its upstream hubs. USBStress randomly chooses the tests and configures the attached test devices. Due to the random nature of the tests, we recommend that you should run USBStress over a 24 hour time period to allow more test combinations.

The tool performs control, bulk, isochronous, data transfers of various transfer lengths to and from the test device. For a SuperMUTT device, USBTCD transfers data to streams supported by a bulk endpoint.

The USBStress driver is largely self-driven, that is, most I/O requests are generated by the driver and not the application. The driver uses timers and work items to generate I/O and perform other operations. The driver checks the registry to determine whether it should run its tests. An external program sets that registry key. The goal of this driver is to create as much concurrency as possible among various operations to flush out race conditions and synchronization issues.

This list summarizes the tests that USBStress performs:

-   Selective suspend with remote wake-up.
-   Concurrent read/write requests on bulk, interrupt, and isochronous endpoints and cancellation.
-   Concurrent strings transfer requests and cancellation.
-   Concurrent abort pipe on bulk endpoints and cancellation .
-   Random reset to surprise-remove and re-enumerate.
-   Random reset to surprise-remove and re-enumerate and fail the re-enumeration.
-   Randomly select an available alternate interface .
-   Randomly instruct the device to stall every nth control transfer .
-   Randomly instruct the MUTT Pack (if connected) to disconnect VBUS from the exposed downstream port.
-   Randomly instruct the MUTT Pack (if connected) to simulate an over-current condition on the exposed downstream port .
-   Randomly instruct the MUTT Pack (if connected) to perform a hardware reset on the hub.

To install the usbstress.sys driver for the MUTT device, use MuttUtil with the `-UpdateDriver `option:

``` syntax
c:\Program Files (x86)\USBTest\x64>MuttUtil.exe -UpdateDriver usbstress.inf
Return value: 0


c:\Program Files (x86)\USBTest\x64>MuttUtil.exe -list
       :    : HARDWARE ID                    :  PROBLEM CODE  : DRIVER
DEVICE :  0 : USB\VID_045E&PID_078E&REV_8011 :             0  : USBSTRESS
Return value: 1
```

## Related topics


[USB test tools](usb-test-tools.md)

[Tools in the MUTT software package](mutt-software-package.md)

[Microsoft USB Test Tool (MUTT) devices](microsoft-usb-test-tool--mutt--devices.md)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Busbcon\buses%5D:%20USBStress%20%20RELEASE:%20%281/26/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



