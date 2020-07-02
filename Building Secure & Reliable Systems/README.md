# Building Secure & Reliable Systems

## Chapter 1

Reliability and security are both crucial components of a truly trustworthy system. Building systems that are both reliable and secure is difficult. While the requirements for reliability and security share many common properties, they also require different design considerations. 

## Design Difference. 

When designing for reliability, you assume that some things will go wrong at some point. When designing for security, you must assume that an adversary could be trying to make things go wrong at any point. In the absence of an adversary, systems often fail safe (or open). But to avoid security vulnerabilities, we could design the door to fail secure and remain closed when not powered.

## Trade Offs

- Redundancy. While redundancy increases reliability, it also increases the attack surface. An adversary need only find a vulnerability in one path to be successful.

- Incident Investigation/Mitigation. Handle security incidents the smallest number of people who can fix the problem effectively, so the security adversary isn’t tipped off to the recovery effort. Voluminous system logs may inform the response to an incident and reduce your time to recovery, but may also be a valuable target for an attacker.

## Confidentiality, Integrity, Availability (CIA) 

These properties are both a reliability and a security concern, just through difference lens. For example, having a push-to-talk microphone stuck in the transmit position is a notable confidentiality problem. A malicious attack may be indistinguishable from a design flaw or a legitimate spike in traffic. 

## Commonalities

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

## Summary 

Chapter 1 gives a high level introduction to security and reliability. It begins with problem statement, then definitions, commonlities and differences of the two. Then design principles from many different angles are discussed at a high level, as well as trade offs between the two concepts.  

## Chapter 2. Understanding Adversaries

In the reliability context, adversaries usually operate with benign intent and take abstract form. By contrast, adversaries in the security context are human; their actions are calcula‐ ted to affect the target system in an undesirable way. In this chapter, we deep dive on security adversaries to help specialists in diverse fields develop an adversarial mindset.

## Attacker Motivations 

Fun. Fame. Activism. Financial gain. Coercion. Manipulation. Espionage. Destruction.

## Attacker Profiles

- **Hobbyists**. 

  - Hobbyists abide by personal ethics about not harming systems and don’t cross boundaries into criminal behavior

- **Vulnerability Researchers.** 

  - Red Teams and penetration testers to make systems better

- **Governments and Law Enforcement.**

  - We recommend that organizations take the long view with regard to building security defenses by investing early in protecting their most sensitive assets, and by having a continued rigorous program that can apply new layers of protections over time. 

- **Activists**. 

  - If your website draw the attention of activists, or allow users to host own content, consider very robust, layered security controls that ensure your sys‐ tems are patched against vulnerabilities and resilient to DoS attacks, and that your backups can restore a system and its data quickly

- **Criminal Actors** 

  - These actors tend to gravitate toward the easiest way to meet their goals with the least up-front cost and effort. Use CAPTCHA to increase the cost of attacks over time. 

- **Automation and Artificial Intelligence.** 

  - Developers need to consider resilient system design by default, and be able to automatically iterate the security posture of their systems.

- **Insiders**

  - First-party insiders. Third-party insiders. Related insiders.

    ![image-20200702132031417](Building Secure & Reliable Systems/images/2-2.png)

  - Threat modeling insider risk

    ![image-20200702132106865](Building Secure & Reliable Systems/images/2-2.png)

  - Designing for insider risk

    - Least privilege. Granting the fewest privileges necessary to perform job duties, both in terms of scope and duration of access. See Chapter 5. 
    - Zero trust. Designing automated or proxy mechanisms for managing systems so that insid‐ ers don’t have broad access that allows them to cause harm. See Chapter 3. 
    - Multi-party authorization. Using technical controls to require more than one person to authorize sensitive actions. See Chapter 5. 
    - Business justifications. Requiring employees to formally document their reason for accessing sensitive data or systems. See Chapter 5.
    - Auditing and detection. Reviewing all access logs and justifications to make sure they’re appropriate. See Chapter 15. 
    - Recoverability. The ability to recover systems after a destructive action, like a disgruntled employee deleting critical files or systems. See Chapter 9.

## Attacker Methods

We discuss a few frameworks for studying attacker methods: threat intelligence, cyber kill chains, and TTPs.

#### Threat Intelligence

Written reports. Indicators of compromise. Malware reports

#### Cyber Kill Chains™

One way of preparing for attacks is to lay out all the possible steps that an attacker may have to take to achieve their goals. 

#### Tactics, Techniques, and Procedures

In short, the framework expands each stage of the cyber kill chain into detailed steps and provides formal descriptions of how an attacker could carry out each stage of an attack. 

## Risk Assessment Considerations

Understanding potential adversaries can be complex and nuanced.

- You may not realize you’re a target.
- Attack sophistication is not a true predictor of success.
- Don’t underestimate your adversary.
- Attribution is hard.
- Attackers aren’t always afraid of being caught.

## Summary 

Chapter 2 narrows down to security adversaries. It begins with defining different attacker motivations and then categorizes attacker profiles into different subsets. It then discusses prevention techniques, methods to understand attacks and of course, trade offs. 







