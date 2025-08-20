<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

## DDoS Attacks on V2G Systems: Attack Methods and Research Insights

DDoS attacks on Vehicle-to-Grid (V2G) systems present a sophisticated and evolving threat landscape that exploits the interconnected nature of electric vehicle charging infrastructure and smart grid communications. Based on recent research and security analysis, these attacks can occur through multiple pathways and employ various technical methods specifically tailored to the unique characteristics of V2G networks.

### Primary DDoS Attack Vectors in V2G Systems

**Request Flooding Attacks** represent the most common form of DDoS targeting V2G infrastructure. Attackers overwhelm charging stations, V2G controllers, and communication servers with massive volumes of legitimate-appearing or malicious requests[^1]. These attacks specifically target the ISO 15118 communication protocol used for EV-to-charging station communication, flooding the SECC (Supply Equipment Communication Controller) with excessive session initiation requests[^1][^2].

Research indicates that DoS attacks account for over 60% of all attacks targeting electric vehicle charging infrastructures, with a dramatic 770% increase observed in network layer DoS attacks during Q4 2023 compared to the previous year[^1]. The attacks exploit the real-time communication requirements of V2G systems, where even brief interruptions can cascade into broader grid instability.

**Resource Exhaustion Attacks** focus on intentionally consuming system resources including CPU, memory, and bandwidth of critical V2G infrastructure components[^1][d grid control systems by creating artificial resource scarcity that prevents legitimate operations. The attacks are particularly effective against V2G systems due to their resource-constrained nature and real-time processing requirements[^3].

**Amplification Attacks** exploit misconfigured protocols within V2G infrastructure to generate traffic volumes significantly larger than the original attack traffic[^4][^5]. Attackers leverage DNS servers, NTP servers, and other network services supporting V2G infrastructure to amplify their attack traffic, creating massive bandwidth consumption that can overwhelm ISP-level infrastructure supporting charging networks[^5].

### Advanced Attack Methodologies

**Botnet-based Coordinated Attacks** represent perhaps the most sophisticated threat to V2G systems. Attackers compromise multiple EV charging stations to form botnets capable of launching synchronized attacks[^6][^7]. Research demonstrates that compromised EVCS botnets can be used to launch attacks against power grid infrastructure, with EV loads having a more significant impact on grid stability than traditional residential loads[^6].

Studies show that a coordinated 30 MW attack utilizing EV loads can completely destabilize a power system, while traditional residential load attacks required 48 MW to achieve similar effects[^6]. This amplified impact occurs due to the high reactive power demand characteristics of EV charging loads and their direct connection to grid control systems.

**Protocol Exploitation Attacks** target vulnerabilities in V2G communication standards, particularly ISO 15118 implementations[^8][^9]. Recent research identified critical vulnerabilities such as CVE-2024-37310 in the EVerest open-source framework, demonstrating integer overflow conditions in V2G Transport Protocol (V2GTP) implementations that can lead to heap overflows and arbitrary code execution[^8].

These protocol-level attacks enable attackers to bypass payment systems, compromise private keys stored in charging stations, and impersonate trusted charging infrastructure in communications with backend systems using OCPP (Open Charge Point Protocol)[^8]. The vulnerability demonstrates how implementation errors in the complex ISO 15118-2 standard can create entry points for sophisticated attacks.

### Multi-Vector Attack Execution Pathways

The execution of DDoS attacks on V2G systems typically follows a sophisticated multi-stage approach:

**Initial Access and Reconnaissance**: Attackers exploit vulnerabilities in publicly accessible charging stations, which often lack adequate physical security and may be located in remote areas without on-site personnel[^8][^10]. Common attack vectors include exploiting weak authentication systems, leveraging physical access points like USB ports, and targeting firmware vulnerabilities in charging station software[^2][^10].

**Infrastructure Mapping and Botnet Formation**: Once initial access is gained, attackers map V2G network topologies to identify critical components such as central aggregators, authentication servers, and grid interface points[^3]. They then install malware on compromised charging stations to create command and control infrastructure for coordinated attacks[^6][^7].

**Coordinated Attack Launch**: Attackers synchronize their botnet to launch attacks during peak charging periods for maximum disruption impact[^6]. They exploit the bidirectional communication nature of V2G systems to amplify attack traffic through grid connections and target critical infrastructure components simultaneously[^1][^3].

### Specialized V2G Attack Techniques

**False Data Injection concealed by DDoS**: Recent research identifies sophisticated attacks where DDoS is used as a cover for false data injection attacks on V2G systems[^11][^12]. Attackers manipulate voltage regulation capacity estimation data while using DDoS traffic to mask their activities and overwhelm detection systems[^11].

**Sybil Attacks with DDoS Components**: Attackers create multiple false vehicle identities within V2G networks while simultaneously launching DDoS attacks to overwhelm authentication systems and prevent detection of the false identities[^13][^14]. These attacks exploit the privacy-preserving pseudonym systems used in V2G communications.

**Replay Attacks Amplified by DDoS**: Attackers capture legitimate V2G communication sessions and replay them en masse to create both authentication confusion and traffic amplification, effectively combining replay attack techniques with DDoS impact[^15][^16].

### Current Research and Detection Approaches

Recent academic research has focused on developing sophisticated detection mechanisms for V2G DDoS attacks. Machine learning approaches, including bio-inspired algorithms like the Grouping Cockroach Classifier (GCC), have achieved detection accuracies of 98.93% in simulated V2G environments[^1][^17]. These systems analyze network flow characteristics, traffic patterns, and protocol anomalies to identify attack signatures.

Deep learning approaches using Convolutional Neural Networks (CNNs) have demonstrated detection precision rates of 99.9% with false alarm rates below 0.1% and average detection times of approximately 2.2 seconds[^18]. However, these solutions require significant computational resources and may face challenges in real-time V2G environments.

### Research Paper Insights

The academic literature reveals several critical insights about DDoS attacks on V2G systems:

1. **"Securing Vehicle-to-Grid Networks: A Bio-Inspired Intrusion Detection System" (2024)**[^1] provides comprehensive analysis of DoS attack prevalence and impact, documenting the dramatic increase in attacks and proposing novel bio-inspired detection mechanisms.
2. **"Central Aggregator Intrusion Detection System for Denial of Service Attacks" (2023)**[^3] demonstrates practical implementation of DDoS detection specifically for V2G central aggregators, showing how network parameters can be manipulated during attacks.
3. **"Electric Vehicle Attack Impact on Power Grid Operation" (2021)**[^6] offers critical insights into how EV-based attacks can be more effective than traditional DDoS attacks due to the unique electrical characteristics of EV loads.
4. **"Cybersecurity in Vehicle-to-Grid (V2G) Systems: A Systematic Review" (2025)**[^19][^20] provides the most comprehensive recent survey of V2G cybersecurity research, analyzing 133 studies and identifying key research gaps in attack recovery and user behavior analysis.
5. **"Detection of cyber attacks in electric vehicle charging systems using remaining useful life approach" (2024)**[^21] introduces novel approaches for estimating attack duration and impact on V2G infrastructure.

The research consistently emphasizes that V2G systems face unique vulnerabilities due to their interconnected nature, real-time communication requirements, and integration with critical power grid infrastructure. The bidirectional communication capability that makes V2G valuable for grid services also creates additional attack vectors that traditional network security approaches may not adequately address.

Current mitigation strategies focus on multi-layered approaches combining network security, authentication improvements, real-time monitoring systems, and machine learning-based anomaly detection. However, the research indicates that recovery mechanisms and user behavior-related security aspects remain significantly under-researched, representing critical gaps in V2G cybersecurity defense strategies.

<div style="text-align: center">⁂</div>

[^1]: https://scientiairanica.sharif.edu/article_23664_39466754746fda04bd9f9118289f89a5.pdf

[^2]: https://h2020response.eu/wp-content/uploads/2023/02/BigData-2022-v02-002.pdf

[^3]: https://www.techscience.com/cmc/v74n2/50252

[^4]: https://www.cloudflare.com/learning/ddos/dns-amplification-ddos-attack/

[^5]: https://www.paloaltonetworks.com/cyberpedia/what-is-a-ddos-attack

[^6]: https://arxiv.org/pdf/2111.11317.pdf

[^7]: https://si.farnell.com/cyber-security-of-ev-charging-stations-trc-ar

[^8]: https://www.darkreading.com/ics-ot-security/ev-charging-stations-still-riddled-with-cybersecurity-vulnerabilities

[^9]: https://www.virta.global/blog/en/blog/how-to-address-the-increasing-threat-of-cyberattacks-on-ev-charging-stations

[^10]: https://www.sstic.org/media/SSTIC2019/SSTIC-actes/v2g_injector_playing_with_electric_cars_and_chargi/SSTIC2019-Article-v2g_injector_playing_with_electric_cars_and_charging_stations_via_powerline-dudek.pdf

[^11]: https://arxiv.org/abs/2203.05087

[^12]: https://www.sciencedirect.com/science/article/pii/S2352467725000220

[^13]: https://arxiv.org/pdf/1905.03507.pdf

[^14]: https://jnao-nu.com/Vol. 15, Issue. 02, July-December : 2024/10_online.pdf

[^15]: https://eprints.bournemouth.ac.uk/28331/1/07880513.pdf

[^16]: https://www.mdpi.com/2079-9292/9/9/1479

[^17]: https://www.aece.ro/abstractplus.php?year=2024\&number=2\&article=4

[^18]: https://www.smart-energy.com/industry-sectors/cybersecurity/does-v2g-pose-a-cyber-threat-to-the-grid/

[^19]: https://arxiv.org/abs/2503.15730

[^20]: https://arxiv.org/html/2503.15730v1

[^21]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11933351/

[^22]: https://journals.sagescience.org/index.php/jamm/article/view/78

[^23]: https://www.tandfonline.com/doi/full/10.1080/23307706.2021.2021113

[^24]: https://sites.google.com/site/neeteshsaxena/cyber-and-critical-infrastructure-security-cycis-lab/research/vehicle-to-grid-security

[^25]: https://www.autocarpro.in/opinion-blogs/securing-the-grid-cybersecurity-innovations-in-v2g-and-ev-energy-exchange-systems-127718

[^26]: https://www.kpit.com/campaign-cyber-security-for-your-smart-charging-system/

[^27]: https://www.sciencedirect.com/science/article/abs/pii/S0306261925010943

[^28]: https://energy.sustainability-directory.com/term/v2g-cybersecurity/

[^29]: https://www.sciencedirect.com/science/article/abs/pii/S0142061522006524

[^30]: https://www.sciencedirect.com/science/article/abs/pii/S0951832022002125

[^31]: https://aece.ro/displaypdf.php?year=2024\&number=2\&article=4

[^32]: https://onlinelibrary.wiley.com/doi/10.1002/oca.3184

[^33]: https://dl.acm.org/doi/10.1016/j.cose.2024.103989

[^34]: https://www.bankinfosecurity.com/electric-vehicle-charging-stations-at-risk-from-hack-attacks-a-26620

[^35]: https://www.sciencedirect.com/science/article/pii/S0167404824002943

[^36]: https://www.sciencedirect.com/science/article/pii/S2090447924002351

[^37]: https://www.mdpi.com/2076-3417/13/13/7391

[^38]: https://www.sciencedirect.com/science/article/abs/pii/S1874548224000349

[^39]: https://www.nature.com/articles/s41598-025-92895-9

[^40]: https://www.sciencedirect.com/science/article/abs/pii/S0140366422004145

[^41]: https://www.sciencedirect.com/science/article/pii/S277267112500018X

[^42]: https://www.mdpi.com/1999-4893/16/2/75

[^43]: https://www.mdpi.com/2224-2708/12/4/51

[^44]: https://rosap.ntl.bts.gov/view/dot/60929/dot_60929_DS1.pdf

[^45]: https://www.mdpi.com/1424-8220/23/3/1683

[^46]: https://www.sciencedirect.com/topics/computer-science/sybil-attack

[^47]: https://www.sciencedirect.com/science/article/abs/pii/S2352467725000785

[^48]: https://www.mdpi.com/1424-8220/24/7/2153

[^49]: https://www.sciencedirect.com/science/article/abs/pii/S2214209624000226

[^50]: https://www.sciencedirect.com/science/article/abs/pii/S2352467725000220

[^51]: https://www.sciencedirect.com/science/article/abs/pii/S0743731513000191

[^52]: https://ietresearch.onlinelibrary.wiley.com/doi/full/10.1049/iet-com.2017.0608

[^53]: https://www.themoonlight.io/en/review/cybersecurity-in-vehicle-to-grid-v2g-systems-a-systematic-review

[^54]: https://www.sciencedirect.com/science/article/pii/S2590174525002703

[^55]: https://www.mdpi.com/2071-1050/14/21/13856

[^56]: https://www.sciencedirect.com/science/article/abs/pii/S0142061521010048

[^57]: https://www.nccoe.nist.gov/projects/cybersecurity-framework-profile-electric-vehicle-extreme-fast-charging-infrastructure

[^58]: https://www.byos.io/img/use-case-securing-ev-charging-networks-against-cyber-attacks.pdf

[^59]: https://bolt.earth/blog/importance-of-cybersecurity-in-ev-ecosystem

[^60]: https://www.mdpi.com/1424-8220/24/1/155

[^61]: https://chargelab.co/blog/why-ev-charger-security-matters

[^62]: https://plaxidityx.com/blog/automotive-cyber-security/ev-cyber-security-plaxidityx-discovers-critical-vulnerability-in-everest-open-source-ev-charging-firmware-stack-cve-2024-37310/

[^63]: https://plaxidityx.com/blog/blog-post/iso-15118-ev-cybersecurity-guide/

[^64]: https://www.sciencedirect.com/science/article/pii/S277315372500012X

[^65]: https://dl.acm.org/doi/10.1145/3704522.3704534

[^66]: https://www.mdpi.com/1996-1073/15/11/3931

[^67]: https://driveelectric.gov/cybersecurity

[^68]: https://arxiv.org/html/2404.06635v2

[^69]: https://www.sciencedirect.com/science/article/abs/pii/S2213138825002668

[^70]: https://ppl-ai-code-interpreter-files.s3.amazonaws.com/web/direct-files/4091bec48ae8266ee8b8bc509b569ade/fbd36a10-e444-4bd0-b4b5-5477ad588f69/0e3ed16e.csv

[^71]: https://ppl-ai-code-interpreter-files.s3.amazonaws.com/web/direct-files/4091bec48ae8266ee8b8bc509b569ade/fbd36a10-e444-4bd0-b4b5-5477ad588f69/243cd963.csv

