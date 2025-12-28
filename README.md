# Riverside Lab

This repository documents a self built Hyper-V home lab based on Windows Server, designed to practice core Active Directory, networking, and support oriented infrastructure concepts in a realistic, multi site environment.

The lab is intentionally scoped as a stable on-premises baseline, reflecting the kind of Windows domain environments commonly encountered in IT support and junior infrastructure roles.

## Purpose and scope

The purpose of this lab is to reinforce practical understanding of:

- Windows Server administration fundamentals
- Active Directory structure and identity management
- DHCP, DNS, and basic routing concepts
- Group Policy usage for baseline configuration
- How infrastructure design surfaces as real world support issues

This repository documents a **completed baseline build**.  
Additional features are intentionally out of scope at this stage.

## Lab overview

The lab consists of:

- A Windows Server 2025 Domain Controller providing:
  - Active Directory Domain Services
  - DNS and DHCP
  - Routing and Remote Access (RRAS) for multi subnet connectivity
- A simulated multi site organisation with four locations:
  - Manchester (HQ)
  - Leeds
  - Liverpool
  - Hull
- Multiple internal subnets connected via RRAS
- A structured Active Directory environment including:
  - Organisational Units (OUs)
  - Security groups
  - Sample user accounts created via PowerShell
- A small set of baseline Group Policies applied at pre-logon and system level

![DC01](01-infrastructure/images/DC01.png)

---

## What is implemented

- Hyper-V host and virtual network configuration
- Domain controller deployment and role configuration
- Active Directory OU and group structure
- DHCP scopes and DNS zones
- Inter-subnet routing using RRAS
- Baseline Group Policy configuration
- PowerShell scripts used during build and configuration

## What is intentionally not implemented

The following areas are documented structurally but are **not implemented in this phase**:

- File server and permission models
- Helpdesk scenario walkthroughs
- Automation workflows beyond initial provisioning
- Monitoring and security tooling

These areas are left as placeholders to support future learning, particularly around:
- Hybrid identity
- Microsoft 365 administration
- Entra ID, MFA, and Conditional Access

## Repository structure

The repository is organised by functional area, with documentation, diagrams, and build scripts grouped accordingly.

Refer to the files in `01-infrastructure` and `02-active-directory` for the core lab configuration, including network design, build steps, and PowerShell scripts used during setup.

```plaintext
riverside-lab/
├── README.md                                       # This file
├── 01-infrastucture/                            # Hyper-V setup documentation
│   ├── build-scripts/                           # PowerShell scripts used in building the system
|   |   ├── 01ImportHyperVandCreate....ps1  
|   |   ├── 02CreateDCVM_Host.ps1
|   |   ├── 03DCNICConfig_DC01.ps1
|   |   ├── 04aRenameandAddRoles_DC01.ps1
|   |   ├── 04bADDSSetup_DC01.ps1
|   |   ├── 05CreateDHCPScopes_DC01.ps1
|   |   ├── 06CreateDNSZones_DC01.ps1
|   |   └── 07RRASSetup_DC01.ps1                    
│   ├── images/
│   ├── 01-environment-setup.md                     # Full description of lab setup
|   ├── 02-hardware-specs.md                        # Lab host machine details
│   ├── 03-ip-addressing-scheme.md                  # IP/subnet breakdown                                
│   ├── 04-build-process.md                         # Step-by-step lab build guide
|   ├── Riverside Physical Topology.drawio.png      # Physical Diagram of what I intend the Lab to simulate
│   └── Riverside Virtual Topology.drawio.png       # Visual Description of the Hyper V Setup used
├── 02-active-directory/                         # AD setup and scripts
│   ├── build-scripts/
|   │   ├── 01CreateOUStructure_DC01.ps1
|   │   ├── 02CreateandNestGroups_DC01.ps1
|   |   └── 03CreateSampleUsers_DC01.ps1   
│   ├── images/
│   ├── 01-ou-structure.md                          # Full description of OU design
│   ├── 02-global-groups.md                         # Full Global Group Design
│   └── 03-sample-users.md                          # User creation and placement plan
├── 03-group-policy/                             # GPO setup and screenshots
│   ├── 02-gpo-inventory/
|   │   ├── README.md
|   │   ├── allow-internal-ping.md
|   │   └── pre-logon-ui-settings.md
│   ├── images/                                             
│   └── 01-security-baseline.md                        
```

## How this lab is used

This lab serves as:

- A reference environment for revisiting core Windows infrastructure concepts
- A safe space for testing identity and access changes
- A foundation for future hybrid identity experiments once Microsoft 365 and Entra ID are introduced

The emphasis is on clarity, documentation, and understanding cause and effect in domain environments.

## Status

This lab is considered **complete at its current scope**.

Any future changes will be additive and driven by specific learning goals rather than roadmap expansion.
