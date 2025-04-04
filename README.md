# README

This repo is for categorizing xss reported on hackerone in 2024.

# Goal

To understand how xss happens today.

In other words, how developers embed XSS vuln in 2024, where more and more developers have been getting careful about security like XSS, and frameworks' protection has been getting prevailed.

# Summary

## sink ratio

|Sink Type|Count|Ratio(%)|Ratio without unknown(%)|
| -- | -- | -- | -- |
|Total|70|100%||
|  HTML DOM|22|31%|51%|
|  HTML Attr escape|10|14%|23%|
|  HTML Attr url|0|0%|0%|
|  JS URL|5|7%|12%|
|  JS Others|2|3%|5%|
|  CSS|0|0%|0%|
|  Others|0|0%|0%|
|  lib vuln|4|6%|9%|
|  unknown|27|39%||

## HTML DOM ratio
| Program|	Count|	Ratio(%)|
| -- | -- | -- | 
| Total|	22|	100%|
| US DoD|	6|	27%|
| mtn|	4|	18%|
| Drugs.com |	2 |	9%|
| Rocket.chat |	2	| 9%|
| Acronis|	1|	5%|
| Mercadolibre|	1|	5%|
| melbadry9|	1|	5%|
| gitlab|	1|	5%|
| Livestream|	1|	5%|
| Github|	1|	5%|
| GoCD|	1|	5%|
| Picsart|	1|	5%|

# Method

## Target

aggregate the 68 reports on H1

- from 2024/1/1 to 2024/12/31
- with diclosed and resolved
- with CWE Cross-Site Scripting
- with severity of Med, High or Critical

https://hackerone.com/hacktivity/overview?queryString=cwe%3A%28%22Cross-Site+Scripting+%28XSS%29%22%29+AND+severity_rating%3A%28%22Critical%22+OR+%22High%22+OR+%22Medium%22%29+AND+substate%3A%28%22Resolved%22%29+AND+disclosed%3Atrue+AND+disclosed_at%3A%3E%3D2024-01-01+AND+disclosed_at%3A%3C%3D2024-12-31&sortField=latest_disclosable_activity_at&sortDirection=DESC&pageIndex=0

## Category

categorize sink into the below categories.

- HTML DOM: DOM is directly injected. For example, using innerHTML.
- HTML Attr Escape: attribute values are escaped with characters like " or ', and then DOM is created.
- HTML Attr URL: javascript scheme is inserted into attributes like iframe src or a href.
- JS URL: URL sink of JS. Typically, functions like window.open or window.location.href.
- JS Others: Other types of JS, such as setTimeout, eval. document.write is also here in this case.
- CSS: from IE era. hasn't been seen in this aggregation.
- Others: things like template injection.
- lib vuln: Vulnerabilities in libraries. The root causes of these library vulnerabilities are not explored here.

**Hackerone report is not source-code-fully-disclosed, so categorization is done by payload analysis.**

**This means this result is affected by how much the reporter has reduced their payload!!**

# Reclaim

The information provided in this research is based on my personal investigation and analysis. While I have made every effort to ensure the accuracy and reliability of the content, I cannot guarantee that all details are correct. The all contents presented are for informational purposes only and should not be taken as definitive or authoritative :)

I am not responsible for any consequences arising from the use or interpretation of this research. Please verify the information independently before relying on it for any decision-making :)

# Spreadsheet

https://docs.google.com/spreadsheets/d/1vbAZWBd_XzZLAYSqFRyDjhp8bkjs3lPa9SFjAcWtn8Q/edit?usp=sharing