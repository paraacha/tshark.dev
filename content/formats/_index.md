---
title: "Pcap Formats"
description: Why have one format when you could have 15?
date: 2019-07-04
author: Ross Jacobs

pre: <b><i class="fa fa-file"></i> </b>
weight: 20
draft: false
---

<a href="/formats/capture_formats"><img src="https://dl.dropboxusercontent.com/s/qcu8n0pyewnzk3r/google_pie_chart.png" alt="Capture Format Comparison" style="width:61%"></a>

{{% notice info %}}
If you are happy with your capture's file type, you can safely skip this section.
{{% /notice %}}

When you send packets to a file or [pipe](/capture/sources/pipe), you
are also sending the packet and file headers. Normally, you will not need
to care about the file format of your packets. This section exists for when it does matter.

You can see just the file
header for any capture type if you capture no packets and send to xxd.
An easy way to capture no packets is to filter by unused [ipx](https://en.wikipedia.org/wiki/Internetwork_Packet_Exchange) in your capture filter.
In this example, we use `-F pcap` for the [pcap](/formats/pcap) file type.

```bash
bash$ tshark -f ipx -a duration:1 -F pcap -w - 2>/dev/null | xxd -u
00000000: D4C3 B2A1 0200 0400 0000 0000 0000 0000  ................
00000010: 0000 0400 0100 0000
```

The first 24 bytes should look like the logo up left ([magic numbers](/formats/magic_numbers) may differ on your system).

<a href="/formats/capture_formats"><img src="https://dl.dropboxusercontent.com/s/txvh306zp3nppuj/logo_pcap_header.png" alt="Derivation of the Tshark Logo" style="text-align:left;margin:0px;margin-left:40px;"></a>

#### Table of Contents

{{% children description="true" depth="4" %}}