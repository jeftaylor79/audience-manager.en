---
description: Describes the required fields, syntax, and conventions used to name an outbound data file.
seo-description: Describes the required fields, syntax, and conventions used to name an outbound data file.
seo-title: Outbound Data File Name  Syntax and Examples
solution: Audience Manager
title: Outbound Data File Name  Syntax and Examples
uuid: effdcaf6-c37c-45f3-9d2f-a938a9da47a6
index: y
internal: n
snippet: y
---

# Outbound Data File Name: Syntax and Examples{#outbound-data-file-name-syntax-and-examples}

Describes the required fields, syntax, and conventions used to name an outbound data file.

## Outbound Data File Name: Syntax and Examples {#concept_C049B849113544CA92EC194A60D0F722}

Describes the required fields, syntax, and conventions used to name an outbound data file.

<!-- 

c_name_reqs_outbound.xml

 -->

>[!NOTE]
>
>The style elements ( `monospaced text`, *italics*, brackets [ ] ( ), etc.) in this document indicate code elements and options. See [Style Conventions for Code and Text Elements](../../../reference/code-style-elements.md#reference_59D0BD0EDB424A65853460D91CCA35D9) for more information.

## Syntax and File Name Elements {#section_9CD8DFD99A994D669103195E25AE968A}

Outbound file names contain the following required and optional elements:

` *`SYNC-TYPE`*_ *`DID`*_ *`MASTER-DPID`*_ *`[PID-ALIAS]`*_ *`SYNC-MODE`*_ *`TIMESTAMP`*[- *`SPLIT_NUMBER`*].sync[.gz]`

**Parameters**

The table defines the elements in an outbound data file name.

<table id="table_1EA97D75004148CE85F702427DB7E97A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> File Name Element </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> SYNC-TYPE </span> </p> </td> 
   <td colname="col2"> <p>Refers to the data transfer methods. Transfer methods include: </p> 
    <ul id="ul_4E0CFC7A34E04E2FA216A07E3654D6EE"> 
     <li id="li_0066B99222A64BE9975AE2E91511FB77">FTP - Transfer using SFTP </li> 
     <li id="li_646767FE8AD247B88D0DD5461349F019"> <span class="keyword"> Amazon S3 </span> - Transfer to <span class="keyword"> Amazon AWS </span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> DID </span> </p> </td> 
   <td colname="col2"> <p>Destination ID. </p> <p>In <span class="keyword"> Audience Manager </span>, a destination is the instance of the integration where you can map your targetable segments. Customers can have multiple destinations, depending on the business requirement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> MASTER-DPID </span> </p> </td> 
   <td colname="col2"> <p>Data-provider or data source ID. This ID identifies the type of User ID present in the file content. Most common User ID keys are: </p> <p> 
     <ul id="ul_CC22D019ECED4B17A7695708001F2C1B"> 
      <li id="li_94DAFA169380405981AFEF1B581997E6">20914 - <span class="keyword"> Google Advertiser ID </span> (raw, unhashed) </li> 
      <li id="li_DE74BE06331C49CF87606A192D815B96">20915 - <span class="keyword"> Apple ID for Advertisers </span> (raw, unhashed) </li> 
      <li id="li_E0A033FEC3174EF08E93EB7C65266337">Vendor ID - 3rd party user IDs (web/cookie) </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> PID-ALIAS </span> </p> </td> 
   <td colname="col2"> The customer identifier from the 3rd party platform. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> SYNC-MODE </span> </p> </td> 
   <td colname="col2"> <p>Sync mode is a macro placeholder that adds a label to the file name based on synchronization type. Synchronization types include full and incremental. They'll appear in the file name as <span class="codeph"> iter </span> or <span class="codeph"> full </span>. </p> 
    <ul id="ul_3B3585CEF1434951B6FDCDD29E5013CD"> 
     <li id="li_947D94E9CFAC4041AC1AAEB191805529"> <span class="codeph"> iter </span>: Indicates an "iterative" or incremental synchronization. An incremental file contains only new data collected since the last synchronization.. </li> 
     <li id="li_13ADB3B3346943DAA767A1F416482D3C"> <span class="codeph"> full </span>: Indicates a "full" synchronization. A fully synchronized file contains old data and any new data collected since the last synchronization. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> TIMESTAMP </span> </p> </td> 
   <td colname="col2"> <p>A 13-digit UNIX timestamp in milliseconds, in the UTC time zone. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> [ <span class="varname"> -SPLIT_NUMBER </span>] </p> </td> 
   <td colname="col2"> <p>An integer. Identifies part of a file that's been split into multiple parts to improve processing times. The number indicates which part of the original file the data belongs to. </p> <p>The original file will not have any split number. The first split file will start with 1. See examples below. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> .gz (optional) </span> </p> </td> 
   <td colname="col2"> <p>GZIP compression. </p> </td> 
  </tr> 
 </tbody> 
</table>

## File Name Examples {#section_487D914CF82043C6A4ADDD772CC0B769}

**Scenario 1**: files sent over to an [!DNL Amazon S3] location, with *`PID-ALIAS="XYZCustomer"`* and with [!DNL Google Advertiser IDs] in the file content.

E.g. incremental files: 

<ul class="simplelist"> 
 <li> <span class="codeph"> S3_1234_20914_XYZCustomer_iter_1486140844000.sync.gz </span> </li> 
 <li> <span class="codeph"> S3_1234_20914_XYZCustomer_iter_1486140844000-1.sync.gz </span> </li> 
 <li> <span class="codeph"> S3_1234_20914_XYZCustomer_iter_1486140844000-10.sync.gz </span> </li> 
</ul>

E.g. full files: 

<ul class="simplelist"> 
 <li> <span class="codeph"> S3_1234_20914_XYZCustomer_full_1486140844000.sync.gz </span> </li> 
 <li> <span class="codeph"> S3_1234_20914_XYZCustomer_full_1486140844000-1.sync.gz </span> </li> 
</ul>

**Scenario 2**: files sent over to FTP location, without *`PID-ALIAS`* and with [!DNL Apple Advertiser IDs] in the file content:

E.g. incremental files: 

<ul class="simplelist"> 
 <li> <span class="codeph"> ftp_1234_20915_iter_1486140843000.sync.gz </span> </li> 
 <li> <span class="codeph"> ftp_1234_20915_iter_1486140843000-1.sync.gz </span> </li> 
</ul>

E.g. full files: 

<ul class="simplelist"> 
 <li> <span class="codeph"> ftp_1234_20915_full_1486140843000.sync.gz </span> </li> 
 <li> <span class="codeph"> ftp_1234_20915_full_1486140843000-1.sync.gz </span> </li> 
</ul>

**Scenario 3**: Files sent over to FTP location, with *`PID-ALIAS="XYZCustomer"`* and with 3rd party User ID in the file content ( *`Vendor ID=45454`*):

E.g. incremental files: 

<ul class="simplelist"> 
 <li> <span class="codeph"> ftp_1234_45454_XYZCustomer_iter_1486140843000.sync.gz </span> </li> 
 <li> <span class="codeph"> ftp_1234_45454_XYZCustomer_iter_1486140843000-1.sync.gz </span> </li> 
 <li> <span class="codeph"> ftp_1234_45454_XYZCustomer_iter_1486140843000-10.sync.gz </span> </li> 
</ul>

E.g. full files: 

<ul class="simplelist"> 
 <li> <span class="codeph"> ftp_1234_45454_XYZCustomer_full_1486140843200.sync.gz </span> </li> 
 <li> <span class="codeph"> ftp_1234_45454_XYZCustomer_full_1486140843200-1.sync.gz </span> </li> 
</ul>

## Outbound Data File Contents: Syntax and Parameters {#concept_6D02DD0812A449388359C11D86D619B5}

Describes the required fields, syntax, and conventions used to organize information in an outbound data file. Format your data according to these specifications.

<!-- 

c_outbound_data_file.xml

 -->

Note: The style elements ( `monospace text`, *italics*, brackets [ ] ( ), etc.) in this document indicate code elements and options. See [Style Conventions for Code and Text Elements](../../../reference/code-style-elements.md#reference_59D0BD0EDB424A65853460D91CCA35D9) for more information.

**Syntax**

Fields in the data file appear in this order:

` *`UUID`*<SPACE> *`SEGMENT_1,SEGMENT_2`*<SPACE> *`REMOVED_SEGMENT_1`*,...`

**Parameters**

The table lists variables that define the contents of a data file.

<table id="table_109BA747CFDA40108370EFEB208C7E11"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parameter </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> UUID </span> </p> </td> 
   <td colname="col2"> <p>A unique user ID assigned by <span class="keyword"> Audience Manager </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> &lt;SPACE&gt; </span> </p> </td> 
   <td colname="col2"> <p>Separate the UUID and segment data with a space </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> SEGMENT_N </span> </p> </td> 
   <td colname="col2"> <p>The segment ID that a visitor belongs to. Separate multiple segments with a comma. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="varname"> REMOVED_SEGMENT_N </span> </p> </td> 
   <td colname="col2"> <p>The segment ID from which the user was disqualified. Separate multiple segments with a comma. With a full synchronization, you can ignore the removed segments because the data file will contain the complete list of current segments for the user. Usually, you want to know about segments a user belongs to rather than those they've been removed from. See also <a href="../../../c-integration/receiving-audience-data/batch-outbound-transfers/outbound-file-name-contents.md#concept_C049B849113544CA92EC194A60D0F722" format="dita" scope="local"> Outbound Data File Name: Syntax and Examples </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Example: Basic File Format**

A properly formatted data file could look similar to the following sample. This file entry indicates a user qualifies for segments 24, 26, and 27. As required, a space separates the UUID and segment IDs. Another space separates the sets of segment IDs. In this example, a user belongs to segments 24, 26, and 27. They've been removed from segments 25 and 28.

```
59767559181262060060278870901087098252  24,26,27  25,28
```
