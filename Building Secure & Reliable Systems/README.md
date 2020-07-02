# Building Secure & Reliable Systems

## Chapter 1

Reliability and security are both crucial components of a truly trustworthy system. Building systems that are both reliable and secure is difficult. While the requirements for reliability and security share many common properties, they also require different design considerations. 

#### Design Difference. 

When designing for reliability, you assume that some things will go wrong at some point. When designing for security, you must assume that an adversary could be trying to make things go wrong at any point. In the absence of an adversary, systems often fail safe (or open). But to avoid security vulnerabilities, we could design the door to fail secure and remain closed when not powered.

#### Trade Offs

- Redundancy. While redundancy increases reliability, it also increases the attack surface. An adversary need only find a vulnerability in one path to be successful.

- Incident Investigation/Mitigation. Handle security incidents the smallest number of people who can fix the problem effectively, so the security adversary isn’t tipped off to the recovery effort. Voluminous system logs may inform the response to an incident and reduce your time to recovery, but may also be a valuable target for an attacker.

#### Confidentiality, Integrity, Availability (CIA) 

These properties are both a reliability and a security concern, just through difference lens. For example, having a push-to-talk microphone stuck in the transmit position is a notable confidentiality problem. A malicious attack may be indistinguishable from a design flaw or a legitimate spike in traffic. 

#### Commonalities

- **Invisibility**. Reliability and security are mostly invisible when everything is going well. Good communication—not only in times of trouble, but also when things are going well—is a solid foundation for this trust. The costs of reliability and security failures can be severe
- **Assessment**. Use riskbased approaches to estimate the costs of negative events, as well as the up-front and opportunity costs of preventing these events. Measure the probability of negative events differently for reliability and security. You can reason about the reliability of a composition of systems and plan engineering work accord‐ ing to desired error budgets. Adversarial testing—simulated attacks typically performed from the perspective of a defined adversary—can also be used to evaluate a system’s resistance to particular kinds of attacks, the effectiveness of attack detection mechanisms, and the potential consequences of attacks. [Chaos Engineering]
- **Simplicity**. A simpler design reduces the attack surface, decreases the potential for unanticipated system interac‐ tions, and makes it easier for humans to comprehend and reason about the system. Understandability is especially valuable during emergencies, when it can help responders mitigate symptoms quickly and reduce mean time to repair (MTTR).
- **Evolution**. New feature requirements, changes in scale, and evolution of the underlying infrastructure all tend to introduce complexity (and accumulate technical debt). On the security side, the need to keep up with evolving attacks and new adversaries can also increase system complexity. The tech debt and complexity can lead to tipping-point situations where a small and apparently innocuous change has major consequences for a system’s reliability or security. 
- **Resilience**. 
  - Unexpectedly high load. Shedding some of the incoming load (processing less) or reducing the processing cost for each request (processing more cheaply)
  - Component failures. Incorporating redundancy and distinct failure domains. Distinct failure domains limit the “blast radius” of a failure and therefore also increase reliability, implemented by compartmentalizing permissions or restricting the scope of credentials. 
  - Encrypte the data not only at storage layer but also at the application layer. 
  - Threats from potential insiders - The principle of least privilege can mitigate insider threats. It dictates that a user should have the mini‐ mal set of privileges required to perform their job at a given time. 
  - Use multi-party authorization to ensure that sensitive operations are reviewed and approved by specific sets of employees. This multi-party mechanism both protects against malicious insiders and reduces the risk of innocent human error, a common cause of reliability failures. 
- **From Design to Production**
  - Design. Spot potential security and reliability issues. Prevent entire classes of problems by using common frameworks and libraries.
  - Test. Normal senarios. Edge cases. Load tests.
  - Deploy. Canaries. System that only accepts properly reviewed code. 
- **Logging**
  - In general, the more complete and detailed your logs, the better—but this guideline has some caveats. At sufficient scale, log volume poses a significant cost, and analyzing logs effectively can become difficult. 
  - Security logs pose an additional challenge: logs typically should not contain sensitive information, such as authentication credentials or personally identifiable information (PII), lest the logs themselves become attractive targets for adversaries.
- **Crisis Response**
  - Well-rehearsed collaboration and good incident management are critical for timely responses in these situations. it’s best to have a plan in place before an emergency occurs. 
  - If an organization is large and the incident requires 24/7 response capabilities or collaboration across time zones, the need to maintain state across teams and to hand off incident manage‐ ment at the boundaries of work shifts further complicates operations.
  - Security incidents also typically entail tension between the impulse to involve all essential parties versus the need—often driven by legal or regulatory requirements—to restrict information sharing on a need-to-know basis. The investigation might grow beyond company bound‐ aries or involve law enforcement agencies.
  - During a crisis, it is essential to have a clear chain of command and a solid set of checklists, playbooks, and protocols.
  - Teams need to keep individuals’ skills and motivation sharp and improve processes and infrastructure in preparation for the next emergency. Frequent offensive security exercises test our defenses and help identify new vulnerabilities. 
- **Recovery**
  - Recovering from a security failure often requires patching systems to fix a vulnerability. It is a double-edged sword: while this capability can help close vulnerabilities quickly, it can also introduce bugs or performance issues that cause a lot of damage.

#### 





#### 

