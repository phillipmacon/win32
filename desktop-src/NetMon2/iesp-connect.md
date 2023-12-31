---
description: The Connect method connects the NPP to the network by using a specified NIC and provides configuration information about the connection.
ms.assetid: 48189b2b-9889-4bd8-8972-26005fb7c341
title: IESP::Connect method (Netmon.h)
ms.topic: reference
ms.date: 05/31/2018
topic_type: 
- APIRef
- kbSyntax
api_name: 
- IESP.Connect
api_type: 
- COM
api_location: 
- Ndisnpp.dll
- Rmtnpp.dll
---

# IESP::Connect method

The **Connect** method connects the NPP to the network by using a specified NIC and provides configuration information about the connection.

## Syntax


```C++
HRESULT STDMETHODCALLTYPE Connect(
  [in]  HBLOB hInputBlob,
  [in]  DWORD StatusCallbackProc,
  [in]  DWORD UserContext,
  [out] HBLOB hErrorBlob
);
```



## Parameters

<dl> <dt>

*hInputBlob* \[in\]
</dt> <dd>

Handle to the BLOB that specifies the NIC that the NPP connects to and the configuration information for that connection.

</dd> <dt>

*StatusCallbackProc* \[in\]
</dt> <dd>

Address of the user's callback function, which receives status updates such as triggers. If a callback function is not used, set this parameter and the *UserContext* parameter to **NULL**.

</dd> <dt>

*UserContext* \[in\]
</dt> <dd>

Value passed when the user's callback function is called. The value of this parameter is typically either HWND or a 'this' pointer. If a callback function is not specified, set this parameter and the *StatusCallbackProc* parameter to **NULL**.

</dd> <dt>

*hErrorBlob* \[out\]
</dt> <dd>

Handle to an error BLOB that contains additional error information.

</dd> </dl>

## Return value

If the method is successful, the return value is NMERR\_SUCCESS.

If the method is unsuccessful, the return value is one of the following error codes (which include those errors returned by the internal **IESP::Configure** call):




| Return code | Description | 
|-------------|-------------|
| <dl><dt><strong>NMERR_ALREADY_CONNECTED</strong></dt></dl> | This instance of the NPP COM object is already connected to the network.<br /> | 
| <dl><dt><strong>NMERR_BLOB_CONVERSION_ERROR</strong></dt></dl> | The configuration BLOB is corrupt. This error is generated by the <strong>IESP::Configure</strong> call.<br /> | 
| <dl><dt><strong>NMERR_BLOB_ENTRY_DOES_NOT_EXIST</strong></dt></dl> | The input BLOB specified by the <em>hInputBlob</em> parameter lacks an entry needed to perform this operation. This error might be generated by the <strong>IESP::Connect</strong> or <strong>IESP::Configure</strong> call. Look at the error BLOB returned by <em>hErrorBlob</em> to determine which entry was not found.<br /> | 
| <dl><dt><strong>NMERR_BLOB_NOT_INITIALIZED</strong></dt></dl> | The <strong>CreateBlob</strong> function has not been called. This error is generated by the <strong>IESP::Configure</strong> call.<br /> | 
| <dl><dt><strong>NMERR_BLOB_STRING_INVALID</strong></dt></dl> | The string is not null-terminated. This error is generated by the <strong>IESP::Configure</strong> call.<br /> | 
| <dl><dt><strong>NMERR_ILLEGAL_TRIGGER</strong></dt></dl> | The trigger portion of the input BLOB is corrupt. This error is generated by the <strong>IESP::Configure</strong> call.<br /> | 
| <dl><dt><strong>NMERR_INVALID_BLOB</strong></dt></dl> | The object specified in <em>hInputBlob</em> is not a BLOB. This error is generated by the <strong>IESP::Configure</strong> call.<br /> | 
| <dl><dt><strong>NMERR_NO_DEFAULT_CAPTURE_DIRECTORY</strong></dt></dl> | The default capture directory was not set in the registry. Use the following path to set the capture directory. <br /><pre class="syntax" data-space="preserve"><code>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\nm\Parameters\CapturePath</code></pre> | 
| <dl><dt><strong>NMERR_OUT_OF_MEMORY</strong></dt></dl> | The memory needed to perform this operation is unavailable. This error is generated by the <strong>IESP::Configure</strong> call.<br /> | 
| <dl><dt><strong>NMERR_TIMEOUT</strong></dt></dl> | The request has timed out. This error is generated by the <strong>IESP::Configure</strong> call.<br /> | 
| <dl><dt><strong>NMERR_UPLEVEL_BLOB</strong></dt></dl> | The version number of the BLOB specified in <em>hInputBlob</em> is incorrect. This error is generated by the <strong>IESP::Configure</strong> call.<br /> | 




 

## Remarks

When the **Connect** method is called, Network Monitor automatically calls **IESP::Configure** by using the BLOB provided by the *hInputBlob* parameter. Note that any error codes returned by the call to **IESP::Configure** are passed back and returned by the **IESP::Connect** call.

This method must be called before you can start capturing frames. Note that when you connect to the network by using this method, you must continue to use the **IESP** interface to capture frames.

The input BLOB specified by *hInputBlob* can be obtained by calling **GetNPPBlobFromUI**, **GetNPPBlobTable**, and **SelectNPPBlobFromTable**.

The error BLOB returned by *hErrorBlob* contains entries that Network Monitor could not understand or find in the input BLOB specified in *hInputBlob*. The returned error BLOB contains error information that the application can use for troubleshooting. For example, if NMERR\_BLOB\_ENTRY\_DOES\_NOT\_EXIST is returned, the entry that Network Monitor could not find is included in the returned error BLOB.



| For information about                          | See                                                                          |
|------------------------------------------------|------------------------------------------------------------------------------|
| Obtaining the input BLOB that represents a NIC | [Selecting a Network Interface Card](selecting-a-network-interface-card.md) |



 

## Requirements



| Requirement | Value |
|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 2000 Professional \[desktop apps only\]<br/>                                                                                               |
| Minimum supported server<br/> | Windows 2000 Server \[desktop apps only\]<br/>                                                                                                     |
| Header<br/>                   | <dl> <dt>Netmon.h</dt> </dl>                                                                      |
| DLL<br/>                      | <dl> <dt>Ndisnpp.dll; </dt> <dt>Rmtnpp.dll</dt> </dl> |



## See also

<dl> <dt>

[IESP](iesp.md)
</dt> <dt>

[IESP::Configure](iesp-configure.md)
</dt> <dt>

[IESP::Disconnect](iesp-disconnect.md)
</dt> <dt>

[IESP::Start](iesp-start.md)
</dt> </dl>

 

 




