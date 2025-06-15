# Risk Decisions 📊

> Risk decisions are about evaluating real residual risk, what's actually exploitable after compensating controls are applied.

## The Standards-Based Decision Framework

Through hundreds of assessments, I've learned that effective risk decisions start with understanding how each organization defines risk through their own minimum security standards.

### 1. Risk = Organizational Standards Violations

**The Foundation:** Every organization defines risk differently based on their:
- Industry requirements
- Regulatory environment  
- Risk appetite
- Security maturity
- Business model

**Common Standards Categories I've Seen:**
- **Healthcare:** Often emphasize HIPAA, medical device security, 24/7 availability
- **Financial:** Focus on PCI-DSS, fraud prevention, transaction integrity
- **Technology:** Prioritize IP protection, development security, API standards
- **Government:** Mandate specific frameworks (NIST, FedRAMP, etc.)

**Examples of How Organizations Define Their Minimums:**
- Some require 8-character passwords, others 16+
- Windows 10 might be minimum for some, Windows 11 for others
- MFA could be required everywhere or just for privileged accounts
- Vulnerability scanning might be monthly, weekly, or continuous

**Key Principle:** Risk is relative to each organization's established standards. What's acceptable at one company might be a showstopper at another.

**My Experience:** At one healthcare organization, their standards included:
- Minimum Windows 10 for all systems
- 16-character passwords (32 for admins)
- Mandatory use of their PRA solution
- Specific encryption requirements

But I've worked with other organizations where the bar was different, some higher, some lower, all based on their unique needs.

### 2. From Identified Risk to Residual Risk

Regardless of the specific standards, the evaluation process remains consistent:

#### 🎯 The Universal Residual Risk Formula

Standards Violation (per org requirements)

Compensating Controls,
Environmental Factors,
Deployment Architecture,
= Residual Risk (Real Risk)

#### 🔍 Real-World Example: Network Vulnerability

**Scenario:** Medical device with unpatched network vulnerability (CVSS 9.8)

**Standard Risk Assessment Would Say:** "Critical - Remote code execution possible"

**Residual Risk Assessment:**
1. **How will it be deployed?** → Isolated VLAN, no internet access
2. **Who can reach it?** → Only specific workstations via firewall rules
3. **What monitoring exists?** → IDS, netflow analysis, anomaly detection
4. **Can exploitation be detected?** → Yes, any unexpected traffic flagged
5. **Real residual risk?** → Low - Would require internal compromise first

**Decision:** Approve with network isolation controls

### 3. Common Compensating Controls That Actually Work

Through experience across different organizations, these controls genuinely reduce residual risk:

#### 🔒 Network Isolation
**Effective For:** Unpatched systems, legacy OS, vulnerable services
- Air-gapped networks for critical legacy systems
- Dedicated VLANs with strict firewall rules  
- No internet access except specific update servers
- Jump box requirements for administrative access

**Real Impact:** Transforms many "critical" vulnerabilities into "low" residual risk

#### 🛡️ Enhanced Monitoring
**Effective For:** Systems that can't be fully secured
- Full packet capture for analysis
- Behavioral anomaly detection
- File integrity monitoring
- Privileged session recording

**Why This Works:** Can't prevent everything, but can detect and respond quickly

#### 🔐 Access Restrictions
**Effective For:** Weak authentication, missing MFA
- Network access controls (802.1X)
- Terminal server isolation
- Time-based access windows
- Location-based restrictions
- IP Whitelisting

**Example:** System with weak passwords but only accessible from nursing stations = manageable risk

#### 📦 Application Control
**Effective For:** Unpatched operating systems
- Application whitelisting (AppLocker/WDAC)
- Privilege restrictions
- Script blocking
- USB controls

**Hypothetical Scenario:** Windows 10 medical device with application whitelisting = acceptable for clinical use

### 4. Making the Decision: A Practical Framework

For each standards violation, I ask:

1. **What's the actual attack vector?**
   - Network accessible? → Isolation possible?
   - Physical access required? → Restricted area?
   - User interaction needed? → Training sufficient?

2. **What compensating controls can be implemented?**
   - Technical controls (most effective)
   - Administrative controls (policies/procedures)
   - Physical controls (location/access)

3. **What's the residual risk after controls?**
   - High → Reject or require remediation
   - Medium → Conditional approval with monitoring
   - Low → Approve with documented controls

4. **Can exploitation be detected?**
   - Yes → Risk often acceptable
   - No → Rarely acceptable regardless of other controls

### 5. Common Decision Patterns

#### ✅ Approve Despite Standards Violations

**Legacy Medical Device Example:**
- Violations: Outdated OS, no antivirus capability, weak passwords
- Compensating Controls:
  - Isolated network segment
  - Application whitelisting deployed
  - Physical access controls
  - Enhanced monitoring
- Residual Risk: Low
- Decision: Approve with controls

**Unpatched But Isolated System:**
- Violations: Multiple unpatched vulnerabilities
- Compensating Controls:
  - No network connectivity at all
  - USB ports disabled
  - Locked server room
- Residual Risk: Very Low  
- Decision: Approve

#### ⚠️ Conditional Approval Examples

**Cloud Platform Missing MFA:**
- Violation: No MFA on admin accounts (org requires it)
- Initial Risk: High (internet-facing)
- Condition: Implement MFA within 60 days
- Interim Control: IP restrictions + audit logging
- Decision: Conditional approval

**Vendor Remote Access:**
- Violation: Requests non-standard remote tool
- Organization's Requirement: Use internal PRA solution
- Condition: Must adopt organization's solution
- Alternative: On-site support only
- Decision: Conditional (comply or no remote access)

#### ❌ Reject - No Compensating Controls Sufficient

**Internet-Facing Legacy System:**
- Violation: Extremely outdated, unsupported OS
- Why No Controls Work:
  - Internet-facing = can't isolate
  - Too vulnerable = patches don't exist
  - No vendor support = can't remediate
- Decision: Reject

**Hardcoded Passwords:**
- Violation: Default credentials, no change possible
- Why Rejected:
  - Can't compensate for hardcoded creds
  - Published in vendor manual
  - Network accessible service
- Decision: Reject until fixed

### 6. Documenting Residual Risk Decisions

**Strong Documentation Template:**

Standard Violated: [Organization's specific requirement]
Business Need: [Why this system/vendor is needed]
Compensating Controls Implemented:

Network: [Specific isolation measures]
Endpoint: [Host-based controls]
Monitoring: [Detection capabilities]
Physical: [Access restrictions]

Residual Risk Assessment: [LOW/MEDIUM/HIGH]

Remote exploitation: [Analysis]
Local exploitation: [Analysis]
Physical access: [Analysis]

Decision: [APPROVE/CONDITIONAL/REJECT]
Conditions: [If conditional]
Review Date: [Ongoing assessment schedule]

### 7. The Real Skill: Risk Contextualization

**What Separates Good Analysts:**
- Understanding how deployment changes risk
- Knowing which controls actually work
- Recognizing when controls aren't sufficient
- Communicating residual risk clearly

**Example Inner Monologue:**
"Yes, this violates the organization's password standard. But it's only accessible from the OR, requires badge access to the room, has session recording, and alerts on any anomaly. The real risk isn't the weak password; it's whether someone could actually exploit it. In this deployment? Aside from insider threat, they can't."

### 8. Adapting to Different Organizations

**What I've Learned:** The same system might result in different decisions at different organizations:

**Organization A (High Security Maturity):**
- Has sophisticated monitoring capabilities
- Can implement complex network isolation
- Decision: Approve with extensive controls

**Organization B (Growing Security Program):**
- Limited monitoring infrastructure
- Basic network segmentation only
- Decision: Defer until security capabilities mature

**Key Insight:** Know your organization's capabilities. Don't approve risks you can't manage.

## 🎭 Real Decision Patterns I've Observed

**The "Scary But Safe" Approval:**
- Device: Critical medical equipment with legacy OS
- Violations: Multiple standards
- Controls: Air-gapped, whitelisted, monitored, physical security
- Residual Risk: Lower than many "compliant" systems
- Result: Years of safe operation

**The "Compliant But Rejected" Scenario:**
- System: Modern cloud platform
- Met Standards: Most technical requirements
- Red Flag: Evasive about data handling
- Investigation: Data processing violated policy
- Decision: Reject (no compensating control for policy violation)

**The "Partnership Success":**
- Vendor: Started with numerous gaps
- Approach: Worked together on remediation
- Timeline: 6-month improvement plan
- Result: Vendor improved security for all their clients

## 🔑 Key Takeaways for Risk Analysts

1. **"Standards violations are the start, not the end."** Real risk depends on exploitability in your environment.

2. **"Know your organization's standards and capabilities."** What works at one company might not at another.

3. **"Compensating controls can transform critical risks to acceptable ones."** But know which controls actually work.

4. **"Network isolation is often your best friend."** Can't hack what you can't reach.

5. **"Document the 'why' behind residual risk decisions."** Future you will thank present you.

6. **"Some risks can't be compensated away."** Know when to hold the line.

7. **"Context is everything."** The same vulnerability can be critical or trivial depending on deployment.

---

**Next:** [Final Thoughts: The Journey Continues →](#final-thoughts-the-journey-continues-)


<br>
<br>
