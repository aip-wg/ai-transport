---
title: "AI Transport Protocol"
docname: draft-aipwg-ai-transport-latest
category: experimental
ipr: TODO
area: TODO
workgroup: AIP-WG
keyword: Internet-Draft, AI, Transport Protocol

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 - name: Okutani Daichi
   organization: FOALK
   email: daichi1616.kytuniv@gmail.com
 - name: Uno Shinichiro
 - name: Yamauchi Taiga
 - name: Gyungwook Lee

normative:
informative:
--- abstract

AIP is designed to provide a framework for seamless integration of AI-powered communication systems, ensuring that AI agents can interact effectively with diverse web resources, facilitate efficient data exchanges, and ensure both factual accuracy and security within transportation protocols. This document outlines the key principles, concepts, and specifications for the AI Transport Protocol (AIP).

--- middle

# Introduction
## Motivation
### Leveraging AI Agents

AI Agents have the potential to revolutionize various domains by automating and enhancing data exchange, decision-making, and interactions with external systems. However, their widespread adoption depends on ensuring that they are equipped with accurate, accessible, and verifiable data. This protocol aims to provide the framework that AI agents can use to interact with data sources effectively while ensuring minimal risk of misinformation and guaranteeing that AI-driven outputs are reliable.

### Factual Integrity
To facilitate the effective use of AI-generated content by humans, it is crucial that the generated information remains highly faithful to factual accuracy. At a minimum, AI agents must ensure that referenced information is neither distorted nor misrepresented, and that the generated content maintains logical consistency. Furthermore, factual integrity is essential for building trust in AI-generated outputs. When AI systems produce content that aligns with verifiable sources without introducing misinformation, users can rely on them with greater confidence. Maintaining factual integrity also reduces the risk of spreading inaccuracies, thereby enhancing the reliability and usability of AI-generated content across various domains.

### Reachability
AI agents are required to generate outputs based on various inputs, including resources that may not be explicitly specified. Therefore, it is essential that all necessary resources are accessible to AI agents and that they are aware of where to obtain specific information. This ensures that AI agents can function effectively, without limitations, in retrieving and processing the data required for accurate outputs.

### Accessibility
Web resources may restrict AI agents from scraping content, particularly for critical components such as advertisements or other important sections of a site. This restriction could result in the inaccessibility of essential data, limiting the AI's ability to function optimally. The protocol addresses these challenges by outlining strategies for AI agents to respect data access rules while still ensuring valuable resources are reachable when needed.

### Traceability
To ensure the reliability and transparency of AI-generated outputs, it is necessary to establish traceability mechanisms. These mechanisms allow for tracking the sources and reasoning behind the data used by AI agents in generating content. This will help verify the quality of the data and provide accountability for the outputs generated, which is crucial in sensitive contexts such as legal, medical, and financial applications.

### Latency
Reducing latency in communication between AI agents and data sources is vital for ensuring responsive and real-time interactions. The protocol establishes guidelines for minimizing latency and ensuring that AI agents can efficiently process and respond to data requests in a timely manner. Optimized transport mechanisms will contribute to lowering delays and improving the overall user experience.

## Purpose
### MCP Server Network
Establish a robust network of Model Content Protocol (MCP) servers to facilitate seamless communication between AI agents and various external data sources. This network will serve as the backbone for enabling efficient data retrieval, processing, and integration into AI systems, ensuring smooth and consistent interactions across different platforms.

### Educational Use of AI
Promote the greater adoption of AI in educational contexts, enhancing learning methods through AI agents that interact with students, provide personalized feedback, and facilitate dynamic learning experiences. AI agents can help create customized educational environments, where students’ progress is tracked and tailored learning paths are provided based on their individual needs.

## Scope
The scope of this document includes the design and specification of a transport protocol that enables AI agents to interact with web resources and external data sources effectively. This protocol ensures that AI agents maintain factual integrity, adhere to access policies, and minimize latency, all while supporting educational and other use cases. It covers the communication mechanisms, data formats, security considerations, and best practices for implementing and utilizing this protocol.

## Terms and Definitions
- **AI Agent**: A system that uses artificial intelligence to process data, generate content, or interact with users and other systems.
- **MCP Server**: A server that implements the Model Content Protocol to facilitate the integration of external data sources with AI applications.
- **Web Resource**: A source of data available on the web, which may include web pages, databases, APIs, or other online content.
- **Transport Protocol**: A protocol designed to facilitate the exchange of data between systems, ensuring efficient and secure communication.
- **Factual Integrity**: The quality of information being true, accurate, and free from distortion or misrepresentation.

# Protocol Overview  

## Basic Concepts  
### Media over QUIC (MOQ)

### Transport
In this protocol, use the MOQTransport protocol for transport, ensuring the secure and efficient transmission of data between AI agents and external systems.

### Session
The session of the MOQ concept.
The MOQ session provides a framework for managing ongoing interactions between AI agents and external data sources, ensuring that context and state are preserved during the communication process.

### Track
A single resource delivered as a "track" within the MOQ system. A track may refer to any distinct data set, file, or content that is used in the protocol’s operations.

### Announcement

### Subscription


### Relay
The MOQ relay is a component that facilitates the transfer of data between AI agents and external resources, ensuring that communication is efficient and reliable.

### Model Content Protocol (MCP)
MCP is an open protocol designed to enable seamless integration between large language model (LLM) applications and external data sources. It facilitates secure data exchanges, improving the accessibility and utility of AI systems.

### Resources
The Resources of the MCP concept.
Every resources maps to a single track.

### Tools
The Tools of the MCP concept.
Functions that can be called by the LLM

### Prompts
The Prompts of the MCP concept.
Pre-written templates that help users accomplish specific tasks

### Verification Levels
- **Individual Comment**: Content generated from individual comments on the web, which may vary in reliability and should be verified for accuracy.
- **Official Pronouncement**: Content generated from authoritative sources, such as government reports or officially published information, which carries a higher level of reliability.
- **MCP Server**: Content sourced from MCP servers, which provide verified and authoritative data for AI systems.
- **Local Resource**: A resource that is located within a local environment, such as a database or file system, providing content that is directly accessible by the AI agent.

## Protocol Architecture  

# Protocol Specification  

## Message Format  
### 

## Transport Mechanisms  

## Security Considerations  

# Implementation Guidelines

## Best Practices

## Performance Considerations

# IANA Considerations

# Security Considerations

# References

## Normative References

## Informative References

# Acknowledgments

---
