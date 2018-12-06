# Service Level Agreement \(SLA\) {#concept_qkz_dm1_wdb .concept}

Service-Level Agreement \(SLA\) "SLA "\) A new version of Ali cloud database \("redis"\) is provided to customers by Ali cloud "\) level of service availability indicators and compensation programmes.

1.  **Definition**

    Service cycle: a service cycle is a natural month, when a customer uses a redis instance for less than a month, the use time of the redis instance is accumulated as a service. cycle.

    Total service cycle minutes: According to 7 \(7\) days per month, 24 \(24\) per day\) hour calculations, when a customer uses a redis instance for less than a month, the redis instance uses a cumulative number of minutes as the service cycle. total number of minutes.

    Service unavailable minutes: When within a minute, all consecutive attempts by the customer to establish a connection with the specified redis instance fail, the redis instance service is considered unavailable for that minute. In a service cycle, the sum of unavailable minutes for a redis instance is the number of minutes for which the service is unavailable.

    \*\*Monthly Service Fee\*\*: This is the sum of all BatchCompute service fees you pay for one calendar month. If a customer prepays an lump sum payment for the service, the Monthly Service Fee equals the lump sum payment divided by the number of service months covered by such payment.

2.  **Service availability**

    Service Availability takes a single instance as a dimension and is calculated as follows:

    Service Availability = \( \(Total service cycle minutes-No service minutes available\)/Total service cycle minutes\) x 100%

    Redis service availability is not less 99.95%, such as redis's failure to meet the above availability commitments, the customer may obtain compensation under article 3rd of this agreement. The scope of compensation does not include the time that the service is unavailable for the following reasons:

    1.  \(1\) Events that result from system maintenance activities by Alibaba Cloud with prior notice, including cutovers, repairs, upgrades, and failure simulation
    2.  \(2\)Any faults or configuration changes on networks or equipment which do not belong to AliCloud.
    3.  \(3\) Events that result from cyberattacks on your applications
    4.  \(4\) Events that result from the loss or leakage of data, tokens, passwords, and other such information due to your improper maintenance or confidentiality
    5.  \(5\) Events that result from your negligence or authorized operations
    6.  \(6\) Events that result from your failure to comply with the Alibaba Cloud product user guides or recommendations
    7.  Caused by resistance.
3.  **Proposed compensation**

    **Standard of compensation 3.1**

    <cf font="Arial" fontcolor="333333"\>Based on the Service Availability of each ApsaraDB for Redis instance in a calendar month, the amount of compensation is calculated in accordance with the standards listed in the following table. As a compensation, we shall provide you with a Service Credit that can be used for purchasing ApsaraDB for Redis products only, and the total Service Credit shall not exceed your Monthly Service Fee \(excluding the fee deducted using a Service Credit\) in the month when the Service Guarantee is not met.

    |Service availability|Compensation voucher amount|
    |--------------------|---------------------------|
    |Less than 99.95% but equal to or higher than 99.00%|15% of monthly service charges|
    |Less than 99.00% but equal to or higher than 95.00%|30% of monthly service charges|
    |Less than 95.00%|100% of monthly service charges|

    **3.2 time limit for application for compensation**

    If you believe that the Service Availability Guarantee for your BatchCompute service has not been met in any calendar month, you can file a claim after the fifth \(5th\) business day of the next calendar month. The application period is limited to the two months following the month when your ApsaraDB for Redis instance fell short of the availability standard. Application beyond this period will not be accepted.

4.  **Other**

    Alibaba Cloud reserves the right to change the terms of this SLA. In the event of any modification to this SLA clause, Ali cloud will be 30 in advance. You are notified by the web site in the form of publicity or sending mail. If you do not agree with the amended version, you have the right to stop using the ApsaraDB for Redis instance. Your continued use of the service after the publication of the amended SLA shall be deemed as your acceptance of the amended SLA.


