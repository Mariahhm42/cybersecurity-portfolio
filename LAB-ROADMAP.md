# SOC Analyst Home Lab Curriculum

A sequenced set of hands-on labs, each building on the last, designed to mirror the real day-to-day of a SOC Analyst: recon → exploitation awareness → traffic/log analysis → SIEM operations → detection engineering → incident response → threat intel → cloud security.

Each lab below has: **the SOC-relevant skill it builds**, **the concept behind it**, **what you'll actually do**, **what goes in the portfolio**, and **the LinkedIn angle**.

---

## Lab 1 — Network Reconnaissance & Scanning
**SOC skill:** Recognizing reconnaissance activity in logs/alerts before an attack even lands.
**Concept:** Every attack starts with recon — discovering live hosts, open ports, running services. If you understand how scans look when you *run* one, you'll immediately recognize one when you're *defending* against it. Maps to MITRE ATT&CK T1595 (Active Scanning).
**What you'll do:** Import Metasploitable2 (deliberately vulnerable target VM) into VirtualBox on an isolated internal network with Kali. Run Nmap ping sweeps, port scans, service/version detection, and OS fingerprinting against it.
**Portfolio:** Scan output screenshots, an explanation of each Nmap flag used and why, MITRE ATT&CK mapping.
**LinkedIn angle:** "Learning to think like an attacker's first move — network reconnaissance with Nmap."

## Lab 2 — Exploitation Basics
**SOC skill:** Recognizing what a successful compromise actually looks like, not just theoretically.
**Concept:** SOC analysts triage alerts about "successful exploitation" constantly — you need a mental model of what's actually happening on the wire and on the host when that occurs.
**What you'll do:** Use Metasploit (built into Kali) to exploit a known vulnerable service on Metasploitable2 (e.g., the vsftpd backdoor or a Samba misconfiguration) and get a shell.
**Portfolio:** Exploitation walkthrough, screenshots, MITRE ATT&CK mapping (Initial Access/Execution techniques).
**LinkedIn angle:** "What does a 'successful exploit' actually look like? I ran one to find out."
**Safety note:** Only ever within your isolated internal network — never against anything internet-facing.

## Lab 3 — Packet Capture & Traffic Analysis
**SOC skill:** Reading raw network traffic to spot malicious patterns — a core Tier-1 SOC task.
**Concept:** This is the pivot point from attacker to defender. The scan and exploit from Labs 1-2 leave a visible fingerprint in packet captures — learning to see it is what separates someone who *ran* an attack from someone who can *detect* one.
**What you'll do:** Capture traffic with Wireshark while re-running the Lab 1 scan and Lab 2 exploit. Filter for SYN scan patterns, follow TCP streams, identify the exploit signature.
**Portfolio:** Annotated packet capture screenshots, the Wireshark filters you used and why.
**LinkedIn angle:** "From attacker to defender: analyzing my own attack traffic in Wireshark."

## Lab 4 — Log Analysis Fundamentals
**SOC skill:** Reading raw logs by hand — before you ever touch a SIEM, you need this foundation.
**Concept:** Every SIEM is built on top of raw logs. If you can't grep an auth log for failed logins, a SIEM dashboard is just a pretty UI you don't actually understand.
**What you'll do:** Generate failed SSH login attempts against a target, then use `grep`/`awk` on the Linux auth logs to find, count, and summarize them.
**Portfolio:** Sample log excerpts plus your written analysis of what you found.
**LinkedIn angle:** "Why every SOC analyst should know grep before they touch Splunk."

## Lab 5 — Build Your SIEM (Wazuh on Oracle Cloud)
**SOC skill:** Actual SIEM operations — the daily tool of every SOC analyst.
**Concept:** A SIEM centralizes logs from many sources and correlates them into alerts. This is the tool you'll live in every single day in a SOC role.
**What you'll do:** Deploy Wazuh manager on a free Oracle Cloud VM, install the Wazuh agent on your own laptop, verify log ingestion, and explore the dashboard.
**Portfolio:** Architecture diagram, setup steps, first screenshots of live data flowing in.
**LinkedIn angle:** "I built and deployed my own SIEM — here's the architecture."
**This is your flagship project.**

## Lab 6 — Detection Engineering
**SOC skill:** Writing and tuning detection rules — moving from "alert consumer" to someone who understands how alerts are made.
**Concept:** Alerts don't appear by magic — someone wrote a rule. Understanding rule logic makes you dramatically better at triage, because you understand *why* an alert fired and what would make it a false positive.
**What you'll do:** Re-run the Lab 1/2 attacks against a Wazuh-monitored target. Write and tune a custom Wazuh detection rule until it correctly fires on your simulated attack.
**Portfolio:** The detection table from your SIEM lab, filled in with real scenario → rule → result data.
**LinkedIn angle:** "I didn't just get an alert — I wrote the rule that generated it."

## Lab 7 — Incident Response Simulation
**SOC skill:** The full IR lifecycle — Identify, Contain, Eradicate, Recover, Lessons Learned — written the way you'd report it to a manager.
**Concept:** Detecting a threat is half the job; responding to it in a structured, documented way is the other half, and it's what interviewers will grill you on.
**What you'll do:** Treat the Lab 6 detection as a real incident. Write a full incident report using the IR lifecycle framework.
**Portfolio:** A formal incident report document — this is one of the most interview-relevant artifacts you can have.
**LinkedIn angle:** "How I responded to my own simulated incident, step by step."

## Lab 8 — Threat Intelligence Enrichment
**SOC skill:** Enriching alerts with external context — a daily task for real analysts.
**Concept:** An IP address or file hash alone tells you little. Checking it against threat intel sources tells you if it's a known bad actor, and how.
**What you'll do:** Take IOCs (IPs, hashes) from Labs 6-7 and enrich them using VirusTotal, AbuseIPDB, and urlscan.io (all free).
**Portfolio:** Enrichment findings added to your Lab 7 incident report.
**LinkedIn angle:** "Every good SOC analyst checks their work against threat intel — here's how."

## Lab 9 — Active Directory Fundamentals
**SOC skill:** Most real-world SOC alerts involve Active Directory (failed logons, Kerberoasting, lateral movement) — you need exposure to this even without a full local domain.
**Concept:** AD is the backbone of most corporate networks; understanding its logs is essential.
**What you'll do:** Given your RAM limits, this one leans on the browser-based platforms (TryHackMe's AD-focused rooms) rather than a local build, plus reading Windows Event Log samples.
**Portfolio:** Notes and a short write-up on common AD attack techniques and what they look like in logs.
**LinkedIn angle:** "Active Directory is everywhere — here's what I learned about defending it."

## Lab 10 — Cloud Security Fundamentals
**SOC skill:** Bridges you toward your longer-term Cloud Security/DevSecOps goal.
**Concept:** Misconfigurations, not just exploits, cause most cloud breaches.
**What you'll do:** On AWS or Azure free tier: harden an overly-permissive IAM policy, detect a misconfigured S3 bucket, and add a basic security scan step to a simple CI/CD pipeline.
**Portfolio:** Before/after configs, screenshots, explanation of each fix.
**LinkedIn angle:** "Most cloud breaches start with a misconfiguration, not a hacker movie moment."

## Capstone — The Full Story
**What you'll do:** Write one cohesive narrative write-up connecting Labs 1 through 8: recon → exploitation → detection → response → enrichment, as a single "day in the life of an incident" story.
**Portfolio:** A polished capstone document — this is the one you lead with when someone visits your GitHub.
**LinkedIn angle:** A multi-part post series, or a single strong recap post tagging your learning community.

---

## How we'll work through this together
For each lab: I'll explain the concept in depth first, walk you through the hands-on steps, ask you to explain it back to me in your own words (this is how we make sure you can talk through it in an interview), then help you write the portfolio entry and draft the LinkedIn post.

**Status:** Kali Linux is installed and ready. Next up: **Lab 1 — Network Reconnaissance & Scanning**, starting with getting Metasploitable2 imported as your target.
