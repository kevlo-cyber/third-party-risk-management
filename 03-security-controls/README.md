# Security Controls 🔐

> Effective security controls are the bridge between identified risks and acceptable business operations.

## Control Frameworks: The Foundation

Throughout my assessments at major healthcare organizations, I've learned that strict adherence to minimum security standards protects both the organization and its patients. Large hospital systems have the leverage to enforce these standards, and vendors adapt.

### 1. Platform-Based Security Requirements

Major healthcare organizations typically categorize their requirements based on where systems are hosted:

#### 🏥 Organization-Hosted Platforms
When systems run within the hospital's infrastructure, organizations can leverage their robust internal controls:
- Enterprise malware protection
- Network segmentation and monitoring
- Centralized vulnerability management
- Managed patching cycles
- Perimeter defenses (IDS/IPS/WAF)

**Key Insight:** Self-hosted systems benefit from defense-in-depth, allowing some flexibility in vendor-specific controls.

#### ☁️ Vendor-Hosted/SaaS Platforms
External systems require stricter scrutiny since they're outside organizational controls:
- Annual third-party penetration testing
- SOC 2 Type II or equivalent certifications
- Detailed vulnerability management programs
- Strong authentication controls
- Comprehensive logging and monitoring

**The Reality:** When you can't control the environment, you must verify the controls.

### 2. Non-Negotiable Security Standards

Based on my experience with major hospital systems, these standards typically aren't optional:

#### 🔐 Authentication & Access Control

**Minimum Requirements I've Enforced:**
- **No default passwords** - Period. Immediate contract blocker
- **16-character minimum** for all passwords
- **32+ characters** for admin accounts (or mandatory rotation)
- **Federation required** - SAML, OAuth, or OpenID for external systems
- **Multi-factor authentication** - Strong MFA for all access
- **Privileged Access Management (PAM)** - All admin accounts protected

**Why This Works:** Major healthcare systems process millions of patient records. Vendors recognize the business opportunity outweighs development costs.

#### 🔒 Remote Access: The Security Maturity Differentiator

**The Organization's Security Investment:**

Having an enterprise Privileged Remote Access (PRA) system demonstrates organizational security maturity. It shows:
- **We've invested in our own security** - Not just demanding from others
- **We understand the risks** - Because we've solved them internally
- **We provide practical solutions** - Not theoretical requirements

**The Only Acceptable Approach:**
- Organization's Privileged Remote Access (PRA) system
- No vendor VPNs or tools - ever
- Alternative: On-site support only

**Why This Position Is Strong:**
When vendors push back on using our PRA system, the conversation goes:
- Vendor: "Our remote tool is secure"
- Us: "We've invested millions in a PRA solution that provides session recording, MFA, and least privilege access"
- Vendor: "But our tool is easier for us"
- Us: "We're providing you enterprise-grade security tools at no cost. This protects both of us."

**The Security Maturity Message:** Organizations that have built robust security infrastructure earn the right to demand vendors meet those standards. We're not asking vendors to figure it out alone; we're providing the tools.

**💡 What I've Learned:** This is where organizational security investment pays dividends. Strong internal controls create leverage for strong vendor controls.

### 3. Technical Control Requirements

#### 🛡️ Encryption Standards

**Enforced Minimums:**
- **At-rest:** AES-256
- **In-transit:** TLS 1.2+ with PFS

#### 🔍 Vulnerability Management

**Requirements by Platform Type:**

**Organization-Hosted:**
- Bi-weekly vulnerability scans (organization-managed)
- Vendor must support patching within CVSS timelines
- Documented mitigation plans for medical devices

**Vendor-Hosted/SaaS:**
- Vendor-provided vulnerability reports every two weeks
- OR annual penetration test attestation
- Evidence of remediation processes

**The Leverage:** When organizations run their own comprehensive vulnerability management programs, vendors can't claim these requirements are unreasonable.

#### 📋 Software Support & Lifecycle

**Absolute Prohibitions:**
- No Windows versions older than Windows 10
- No end-of-life (EoL) operating systems
- No end-of-support (EoS) software
- No unsupported components

**Common Challenge:** Medical devices running Windows 7 or older
**Standard Resolution:** Contract rejection unless vendor provides upgrade timeline to Windows 10+ before implementation

**The Hard Line:** I've seen vendors lose hefty contracts over Windows 7. The message was clear: upgrade or walk away.

### 4. Compliance & Audit Requirements

#### 📊 Evidence Requirements

**What Strong Vendors Provide Without Hesitation:**
- Current SOC 2 Type II reports
- Penetration test executive summaries
- Vulnerability scan reports (appropriately redacted)
- Policy and procedure documentation
- SBOM (Software Bill of Materials) or MDS2 forms

**Red Flag:** "We can't share our security documentation due to security concerns"

**Our Response:** "We share our security posture through certifications and attestations. We expect the same transparency."

### 5. The Power of Organizational Standards

**Why Strict Standards Work:**

When dealing with major healthcare systems that have invested heavily in security:
- Vendors see a mature security program worth aligning with
- The organization's tools and processes make compliance easier
- Standards come with solutions, not just requirements
- Future vendor relationships start from a higher baseline

**The Multiplier Effect:** Organizations with strong security programs don't just protect themselves; they elevate the entire vendor ecosystem.

**Personal Satisfaction:** Knowing that every vendor who meets these standards improves their security for all their customers creates real-world impact.

## 🎭 Real Patterns: From Rejection to Compliance

**Pattern 1: The Quick Learner**
- Initial submission: Multiple control gaps
- First discussion: "These are our standards, and here are our tools to help you meet them"
- Two weeks later: "We've enrolled in your PRA system and implemented MFA"
- Result: Compliant within 60 days

**Pattern 2: The Security Partnership**
- Initial submission: "How does your PRA system work?"
- Our response: Technical walkthrough and support
- Vendor feedback: "This is better than our current approach"
- Result: Vendor adopts similar standards for other clients

**Pattern 3: The Wake-Up Call**
- Initial submission: Running Windows 7
- Our response: "This shows fundamental security gaps"
- Vendor realization: They're behind industry standards
- Result: Complete security program overhaul or lost opportunity

## 🔧 When Compensating Controls Aren't Enough

Some gaps simply can't be compensated:

**Example: Legacy Medical Device**
- **Vendor Claim:** "It only runs on Windows XP"
- **Our Response:** "Then it doesn't run here"
- **Vendor Escalation:** "But it's FDA approved"
- **Final Answer:** "FDA approval doesn't override security requirements"

**Result:** Vendors either found upgrade paths or lost the business.

**Key Principle:** Organizations that have invested in modern security infrastructure set the standard for their vendors.

## 🔑 Key Takeaways for Risk Analysts

1. **"Strong internal security creates vendor leverage."** Organizations that invest in tools like PRA and PAM earn the authority to demand high standards.

2. **"We provide solutions, not just requirements."** Mature organizations offer vendors the tools to succeed.

3. **"Self-hosted vs. vendor-hosted determines scrutiny level."** Internal controls reduce risk for on-premise systems.

4. **"Remote access reveals security maturity, theirs and ours."** How both parties handle privileged access shows their true security posture.

5. **"Some risks can't be compensated away."** Windows 7 and older? No amount of controls makes that acceptable.

6. **"Creating industry-wide impact through individual assessments."** Every vendor forced to improve makes healthcare more secure.

---

**Next:** [Risk Decisions →](#risk-decisions-)
