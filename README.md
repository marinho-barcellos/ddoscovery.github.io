# DDoS-landscape-reports

This repository contains a 2022 DDoS reports analysis spreadsheet, available in different formats (the main format we recommend is PDF or HTML, because of the formatting) and the report files used in the analysis.

**Page info.**
In the spreadsheet, we add page number information (e.g. "p3:") to allow the reader to easily locate the information in the original document.
However, we could only provide page numbers for PDFs, since the HTML file does not have the distinction of pages.
In the case of HTML, we indicate names of sections whenever possible.

**URLs.**
We include URL links to the online versions in the FORMAT column.
Please note that vendors may update the page/file or remove the content without notice.
To prevent the loss of information, we provide a snapshot of the information collected. The reports were collected between February 2023 and February 2024.

**Format.**
Text in _italics_ represents our interpretation/view, while **bold** is used for highlighting. The table spans three pages, with an additional page/row with a global analysis for each column.

## Table
The table has the following columns.

### VENDOR
The identification of the business or organisation issuing the report.
This may be different kinds of organisations for DDoS mitigation: DDoS mitigation provider (e.g. Imperva);
technology vendor (e.g. Netscout); CDN-based (e.g. Akamai); Cloud provider (e.g. AWS, Microsoft); or
NGOs (e.g. NBIP).

### SUMMARY
Provides a short description of what the document is, such as a 2022 landscape report or a longitudinal discussion of vector prevalence.
It includes comments about salient features, such as if results are separated according to layers (L3, L4 and L7).

### TITLE
The title of the document/report.

### FORMAT
The column indicates whether the report is offered as a webpage or a PDF/image, and if completing a contact form is a condition to get access (Open/Closed).

### PERIOD
The (main) period analysed by the report, which is not always clear.
Some reports focus on a period but draw comparisons with other periods (one or more quarters back, one or more years back, such as "since 2019, there has been an increase of X%").
Most reports focus on 1-year period; we use 2022 reports whenever available, and occasionally, covering 2021 or 2023, and clearly note when this is the case.

### ATTACK COUNTS
The number of attacks in the period (say, year) is one of the most common metrics presented by reports.
Some reports present the information as rates (e.g. attacks per day) instead of the total number.
The number of attacks depends on the length of the period covered, the season (e.g. prior to Black Friday), the existence of geopolitical conflicts, etc.
For example, the Russian DDoS mitigation provider saw a sharp increase in the number of attacks because of the conflict between Russia and Ukraine.

### R/A
This column provides information about the prevalence of reflection/amplification attack vectors.
Examples of vectors that are often mentioned are: NTP amplification, DNS amplification, Memcached, and occasionally, TCP amplification.
Some reports do not specify clearly if DNS refers to a L7 attack against DNS (e.g. water torture) or exploiting DNS for a volumetric attack (amplification).
The most common value shown is the percentage of attacks that used NTP, DNS, Memcached, SSDP, etc.
The fraction is often presented relative to the R/A type, and the total R/A fraction is not given.
Whenever the information is available in the report, the column shows the _trend_ (increase, decrease) of the vector, however in almost all cases the numbers are presented _just_ for the vector, not for the entire class.
Unless noted, we do not look at multiple consecutive reports to compare the numbers and extract trends.

### D/P
This column provides information about the prevalence of direct-path attack vectors (e.g. NTP amplification, DNS amplification, Memcached, and occasionally, TCP amplification).
Examples of vectors that are often mentioned are variants of ``floods``: TCP SYN flood, TCP ACK flood, UDP flood, HTTP flood (of requests), DNS flood (of queries), etc.
Like R/A, with D/P the numbers usually refer to _individual_ vectors, omitting the fractions of D/P and R/A attacks, so we cannot infer when there was an increase or decrease of R/A and D/P.
To illustrate, a report may state that there was an increase in the use of HTTPS attacks; assuming that this attack is a form of D/P (with or without proxies), we _cannot infer_ that there was a general increase in the proportion of D/P attacks (compared to R/A attacks).

### VECTORS
This column contains additional information about the attack vectors in the report.
For example, when the information is considered relevant, but we could not confidently assign it to the R/A or D/P columns.

### CHANGES END OF 2022
The column reports changes in metrics throughout the year, with special interest on the final months of 2022.
We wanted to see if there were general reductions in attack levels or at least reduction in specific types, reflecting the collaborative efforts to mitigate DDoS (e.g. the booters shutdown or the DDoS Traceback Working Group).

### ATTACK DURATION/SIZE
Many reports analyse the duration of attacks, measured in minutes, hours or days.
Some (few) reports also present (or instead) the volume (bits) of attacks as the ``size``.
The duration of attacks is affected by the methodology employed to count attacks; depending on the maximum interval between packets within an attack, a single longer attack can be counted as multiple smaller attacks.
This is specially the case with pulse-wave attacks, which is based on bursts of packets.
Unfortunately, but unsurprisingly, the reports vary in how they group the attacks in buckets or intervals (e.g. ``up to 10 minutes``, ``between 10 and 30 minutes``, etc., which prevents a comparison with other reports.


### ATTACK INTENSITY
The column shows the peak or maximum bandwidth, packet rate, or request/query rate that any single attack achieved.
The information is relevant in order to dimension the resources effectively against attacks, such as the capacity of links to transmit all the volume to the destination network, the capacity of routers or firewalls to deal with high packet rates, and of servers to deal with a high rate of requests/queries.
Like duration/size, the reports vary in how they group the attacks in buckets or intervals, which prevents a comparison with other reports.
Some reports state that the majority of attacks are of low intensity, which can be implied as a good thing, but actually the issue is more complex because L7 attacks may cause more damage with lower volume/rates.

### CARPET BOMBING
Carpet bombing is a technique used to make (threshold-based) mitigation harder.
Instead of sending packets to a single IP address, the attacker uses a range of IP addresses part of the attacked network.
The technique is also known as ``horizontal attacks``, ``prefix attacks``, or ``bit-and-piece`` attacks.

### MULTI-VECTOR
This column provides information about the combination of vectors in the same attack.
The multiple vectors used may be similar (e.g. TCP SYN flood and UDP flood) or very different (e.g. DNS amplification combined with TCP SYN).
We note that the numbers vary substantially among reports and among periods (from one year to the next, the situation changes completely).

### TARGET
Some of the reports contain geographic information, such as how attacks are distributed in the globe, e.g. per country or per region.
Others breakdown attacks per Industry attacked, such as Telecom (ISPs), Finance, Online Gaming, and Education.
The set of Industry categories chosen, unsurprisingly, varies considerably among reports.

### VANTAGE POINTS/SOURCES
This column contains information about how the attack data was collected, i.e. from which (kind of) networks (ISPs, enterprises) and where (region, global).
There are also comments about other sources of information, such as scanning or more generally, threat intelligence.
