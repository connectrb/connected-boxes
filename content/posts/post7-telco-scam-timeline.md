---
title: "Post#7: Scam Prevention, Detection and Disruption"
date: 2026-04-19T17:08:29+10:00
draft: false

---

Scams are obviously a nightmare, but the deeper I dig into this, the more I’m struck by the sheer scale of what they’re pulling off. It’s wild—and honestly terrifying — how easily traditional identity checks just fall apart the second a scammer pulls out a stolen passport. And they seem to have an endless supply of them. The odds are stacked against us: every time a Telco manages to flag and block an account, scammers just swap it out for a fresh, stolen identity and keep going. The resilience of stolen passports supply chain is just staggering.

I wanted to share my understanding of how new SPF regulation is panning out for Telcos. Today I will touch on requirements to prevent, detect and disrupt.

---

## Legally, what is a scam

Scam definition is pretty straightforward: 

- An attempt to deceive a consumer into making a payment to a scammer using a regulated service, such as a bank transfer.
- An attempt to deceive a consumer into giving personal information to a scammer using a regulated service, such as a phishing scam on a direct messaging app.

These are considered scams even where they are not successful and do not lead to a loss. 

Today I want to look at different layers of protections Telcos are building to increase friction for scammers. These layers are - 
- PREVENT
- DETECT
- DISRUPT

![SPF-Layers](/images/posts/spf-friction-layers.png)
*Scam Prevention Framework Friction Layers*

---

## Prevent Scenarios

Telcos must utilise their technical capabilities to stop scammers from reaching consumers through their network.

### Legitimate Use Case Verification

Telcos must check that customer - usually a business - has an honest and valid reason before they are allowed to use certain advanced calling features. There is technology that allows a caller to "mask" their real phone number and make a different number appear on your screen (this is often how "spoofing" works). Scammers use this to pretend to be someone you trust, like the Police, ATO or a well-known business (like AusPost).

**A Simple Example**

- The Honest Business: A large real estate agency wants to make calls from fifty different mobile phones, but they want every customer’s caller ID to show the agency's one main office number. This is a legitimate use case. The telco verifies the agency is real and owns that main number, then allows the service.
- The Scammer: A criminal sets up a business account and asks for the power to make their outgoing calls look like they are coming from "ATO (Australian Tax Office)". Because the telco is now required to verify the legitimate use case, they would see the applicant has no connection to the bank and refuse to provide the service.

### Phishing Content Filtering

Telcos must implement anti-scam filters designed to identify and block SMS messages that contain malicious phishing links. 

Current generation SMS and MMS firewalls are very smart - they perform real-time, deep-packet inspection of signalling traffic. They analyse the origin, content, and routing of every message. 

URL Scanning Modules are Integrated directly into the firewall, these scanners check links embedded in SMS messages against real-time blacklists of known malicious, fraudulent, or recently registered "parked" domains used in phishing campaigns.

### Brand and Number Protection

Telcos must now take practical steps to stop scammers from pretending to be a trusted business to trick us. There are two main parts of this requirement - 

- Protect their own brand: A Telco must make sure criminals cannot use Telco's own name or official numbers to send scam messages to its customers. 
- Prevent "Spoofing": Telcos must use technology to stop scammers from faking (or "spoofing") the phone numbers of other legitimate businesses. 

**A Simple Example**

Imagine a scammer wants to send out thousands of text messages that look like they are from "Australia Post" telling people there is a "problem with a delivery".

Under these rules, the telco must have systems in place to:

- Identify that these messages are not actually coming from the real Australia Post.
- Block these "spoofed" messages so they never show up on your phone.
- Use registries, such as a government-funded SMS sender ID registry, to verify that only the real business is allowed to use that specific name in a text message.

> With the SMS Sender ID Register becoming mandatory on July 1, 2026, telcos will soon be required to block or tag messages. Any branded SMS (e.g., from 'AusPost') not verified on the registry by this date will be delivered with an 'Unverified' label or blocked entirely to prevent impersonation.

By taking these steps before the scam reaches you, the telco prevents you from ever seeing the fake message and being tricked by it.

### Consumer Education

Maintaining a scam awareness webpage and providing easy referrals to national resources like Scamwatch to educate users on recent trends.

---

## Detect Scenarios

Let's look at the scenarios which involve the active monitoring of network traffic to identify suspicious behaviour.

### Traffic Pattern Analysis

Since Telcos are the pipes through which the scammer traffic flows, Telcos must constantly endeavour to identify suspicious behaviours based on the traffic.

- Patterns of bulk communications sent from a new number or device.
- Unusual or sudden increase in call volume from a specific number.
- Repeated short-duration calls, which often indicated automated "robocalling"
- Communications originating from invalid numbers or those on "do not originate" list.

### Identification of Engaged Victims  

Telcos not only have to identify the scammers, they must also have systems to identify the customers who have engaged with a suspected scammer, such as those who returned a text message or spent time speaking with them on a call.

---

## Disrupt Scenarios

Scenarios that involve taking decisive action once a scam threat is identified or reported.

### CLI Blocking and Withdrawal

Telcos must block calls and messages from Calling Line Identifiers (CLIs) confirmed to be scams. During an ongoing investigation, they may temporarily withdraw the CLI to stop further engagement while they verify the threat.

### Traceback Cooperation 

Telcos are required to cooperate with other providers and the regulator to trace the origin of suspected scam calls across different networks.

> **Safe Harbour Protections:** To encourage aggressive disruption, the Act provides a 28-day 'safe harbour' period. This protects telcos from being sued for damages by a customer (or a business) if the telco mistakenly blocks a service while investigating a high-risk scam lead, provided they act in good faith.

### Acting on Shared Actionable Scam Intelligence (ASI)

While telcos may share intelligence via industry hubs like the AFCX operationally, the legal requirement under the SPF is to report it to the ACCC/National Anti-Scam Centre, who then disseminate it across the ecosystem. Similarly, once scam intelligence is available from other source like digital or financial organisations, the telco will use the intelligence to block the reported number across the entire network, preventing hundreds of other potential victims from being contacted.

---

## Is this enough?

Here's the thing though — for every barrier we put up, the scammers adapt. They swap SIMs, rotate numbers, shift to new platforms. The supply chain of stolen identities is relentless. But that's exactly why these layered defences matter: no single measure is perfect, but together they increase the friction high enough that many scammers move on to easier targets.

The biggest shift isn't just technical; it's financial. Under the SPF, if a telco fails to take 'reasonable steps' to prevent a scam that was detectable, they can now be held liable to compensate the victim for their losses. This 'shared liability' model ensures the cost of failure sits with the providers, not just the victims.

What do you think — is regulation the answer, or is there a deeper shift needed to protect people from themselves?