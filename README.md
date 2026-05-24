# BGP Routing Security Lab: RPKI and ASPA Evaluation

## Overview

This project implements an emulated inter-domain routing security laboratory using BGP to study fundamental Internet routing vulnerabilities and their mitigations.

The lab focuses on analyzing:
- Prefix hijacking and sub-prefix hijacking
- BGP route leaks
- AS-PATH manipulation attacks
- Impact of routing misconfigurations on inter-domain routing stability

It further evaluates modern security mechanisms including:
- Resource Public Key Infrastructure (RPKI)
- Route Origin Validation (ROV)
- AS Provider Authorization (ASPA)

## Problem Statement

The Border Gateway Protocol (BGP) operates on an implicit trust model, lacking cryptographic verification of routing information. This leads to vulnerabilities such as prefix hijacks and route leaks, where malicious or misconfigured Autonomous Systems can disrupt global routing behavior.

While RPKI provides origin validation, it does not fully protect against path-based attacks, motivating the need for ASPA-based validation.

## Objectives

- Demonstrate BGP prefix hijacking scenarios in a controlled environment
- Simulate route leak propagation across Autonomous Systems
- Evaluate the effectiveness of RPKI-based origin validation (Valid / Invalid / Unknown states)
- Study limitations of RPKI in path-based attack scenarios
- Implement and analyze ASPA-based mitigation techniques

## Methodology

The experimental environment is built using:

- Kathará network emulator
- Docker-based virtual Autonomous Systems
- OpenBGPD routing daemon
- RPKI validator infrastructure

The topology simulates multi-homed AS environments and Internet Exchange Point (IXP) behavior to replicate real-world routing dynamics.

## Attack Scenarios

The lab reproduces:

- Prefix Hijack: Unauthorized origin announcement of IP prefixes
- Sub-Prefix Hijack: More-specific prefix advertisement overriding legitimate routes
- Route Leak: Improper propagation of learned routes beyond intended AS boundaries
- AS-PATH Manipulation: Forged or altered path attributes to influence routing decisions

## Security Mechanisms Evaluated

### RPKI (Route Origin Validation)
- Validates whether an AS is authorized to originate a prefix
- Classifies routes as:
  - VALID
  - INVALID
  - NOT FOUND

### ASPA (AS Provider Authorization)
- Validates AS path relationships
- Reduces impact of route leaks and forged path attacks
- Strengthens inter-domain routing trust model

## Architecture

The system uses a hierarchical AS topology where a central transit AS (AS65001) interacts with multiple customer and peer networks to simulate real-world routing behavior.

## Results

The experiments demonstrate:
- BGP’s vulnerability under trust-based routing
- Effectiveness of RPKI in mitigating origin hijacks
- Remaining gaps in path validation without ASPA
- Improved routing stability when both RPKI and ASPA are deployed

## Project Structure
