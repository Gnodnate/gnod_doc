---
layout: post
title: Software development of USB
---

由于对于笔者来说，USB过于复杂（至少在software这边比Network要复杂），而且自己的记性又不是太好，所以，这次在修改Mac下USB通讯问题，顺便把USB知识总结一下。


USB Requests
<!-- 
|**Offset**| **Field**     |*Size*| *Value*         |*Description*                                         |
|:--------:|:-------------:|:----:|:---------------|------------------------------------------------------|
| 0        | bmRequestType | 1    | Bitmap          | Characteristics of request:                          |
|          |               |      |                 | D7: Data transfer direction                          |
|          |               |      |                 | 0 = Host-to-device                                   |
|          |               |      |                 | 1 = Device-to-host                                   |
|          |               |      |                 | D6...5: Type                                         |
|          |               |      |                 | 0 = Standard                                         |
|          |               |      |                 | 1 = Class                                            |
|          |               |      |                 | 2 = Vendor                                           |
|          |               |      |                 | 3 = Reserved                                         |
| 1        | bRequest      | 1    | Value           | Specific request (refer to Table 9-3)                |
| 2        | wValue        | 2    | Value           | Word-sized field that varies according to request    |
| 3        | wIndex        | 2    | Index or Offset | Word-sized field that varies according to request;   |
|          |               |      |                 | typically used to pass an index or offset            |
| 4        | wLength       | 2    | Count           | Number of bytes to transfer if there is a Data stage |
-->

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;border-color:#ccc;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#ccc;color:#333;background-color:#fff;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#ccc;color:#333;background-color:#f0f0f0;}
.tg .tg-9hbo{font-weight:bold;vertical-align:top}
.tg .tg-amwm{font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-l2oz{font-weight:bold;text-align:right;vertical-align:top}
.tg .tg-yw4l{vertical-align:top}
.tg .tg-dzk6{background-color:#f9f9f9;text-align:center;vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-9hbo">Offset</th>
    <th class="tg-amwm">Field</th>
    <th class="tg-l2oz">Size</th>
    <th class="tg-amwm">Value</th>
    <th class="tg-9hbo">Description</th>
  </tr>
  <tr>
    <td class="tg-yw4l">0</td>
    <td class="tg-dzk6">bmRequestType</td>
    <td class="tg-yw4l">1</td>
    <td class="tg-dzk6">Bitmap</td>
    <td class="tg-yw4l">Characteristics of request<br>D7: Data transfer direction<br>      0 = Host-to-device <br>      1 = Device-to-host<br>D6...5: Type <br>           0 = Standard<br>           1 = Class <br>           2 = Vendor <br>           3 = Reserved<br>D4...0: Recipient <br>           0 = Device<br>          1 = Interface <br>          2 = Endpoint<br>          3 = Other<br>          4...31 = Reserved</td>
  </tr>
  <tr>
    <td class="tg-yw4l">1</td>
    <td class="tg-dzk6">bRequest</td>
    <td class="tg-yw4l">1</td>
    <td class="tg-dzk6">Value</td>
    <td class="tg-yw4l">Specific request (refer to Table 9-3)</td>
  </tr>
  <tr>
    <td class="tg-yw4l">2</td>
    <td class="tg-dzk6">wValue</td>
    <td class="tg-yw4l">2</td>
    <td class="tg-dzk6">Value</td>
    <td class="tg-yw4l">Word-sized field that varies according to<br>request</td>
  </tr>
  <tr>
    <td class="tg-yw4l">3</td>
    <td class="tg-dzk6">wIndex</td>
    <td class="tg-yw4l">2</td>
    <td class="tg-dzk6">Index or<br>Offset</td>
    <td class="tg-yw4l">Word-sized field that varies according to<br>request; typically used to pass an index or<br>offset</td>
  </tr>
  <tr>
    <td class="tg-yw4l">4</td>
    <td class="tg-dzk6">wLength</td>
    <td class="tg-yw4l">2</td>
    <td class="tg-dzk6">Count</td>
    <td class="tg-yw4l">Number of bytes to transfer if there is a<br>Data stage</td>
  </tr>
</table>
