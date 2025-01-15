---
title: "AI Transport Protocol"
docname: draft-aipwg-ai-transport-latest
category: exp
workgroup: AIP-WG
keyword: Internet-Draft, AI, Transport Protocol

submissionType: independent
ipr: none

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 - name: Okutani Daichi
   organization: FOALK
   email: daichi1616.kytuniv@gmail.com

normative:
informative:

--- abstract

AIP is designed to provide a framework for seamless integration of AI-powered communication systems, ensuring that AI agents can interact effectively with diverse web resources, facilitate efficient data exchanges, and ensure both factual accuracy and security within transportation protocols. This document outlines the key principles, concepts, and specifications for the AI Transport Protocol (AIP).

--- middle

# Introduction

## Motivation

### Leveraging AI

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

### Large Integrated Resource

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

# Concepts

## Media over QUIC's Concepts

Media over QUIC (MOQ) is a live media protocol powered by QUIC

### Transport

In this protocol, use the MOQTransport protocol for transport, ensuring the secure and efficient transmission of data between AI agents and external systems.

### Session

The session of the MOQ concept.
The MOQ session provides a framework for managing ongoing interactions between AI agents and external data sources, ensuring that context and state are preserved during the communication process.

### Track

A single resource delivered as a "track" within the MOQ system. A track may refer to any distinct data set, file, or content that is used in the protocol’s operations.

### Group

A group is a set of data sent in a single QUIC stream.

### Announcement

The MOQ's Announcement.
It indicates where endpoints can find resources such as MCP server.

### Subscription

The MOQ's Subscription.
A single subscription is a single resource.

### Fetch Request

The MOQ's Fetch Request.
Endpoints send request to the other as the MOQ's Fetch Request.
Thus request and responce will be negotiated on a single QUIC stream.

### Relay

The MOQ relay is a component that facilitates the transfer of data between AI agents and external resources, ensuring that communication is efficient and reliable.

## Model Content Protocol Concepts

Model Content Protocol (MCP) is an open protocol designed to enable seamless integration between large language model (LLM) applications and external data sources. It facilitates secure data exchanges, improving the accessibility and utility of AI systems.

### MCP Server

MCP servers provides information from resources to MCP clients

### MCP Client

MCP clients comminucate with MCP servers and accesses to modified resources through the server.

### Resources

The Resources of the MCP concept.
Every resources maps to a single track.

### Tools

The Tools of the MCP concept.
Functions that can be called by the LLM

### Prompts

The Prompts of the MCP concept.
Pre-written templates that help users accomplish specific tasks

## Request-Responce

A endpoint request to the other endpoint with REQUEST message. The other endpoint verifies if they has a method matches to the Method Name and handles the Parameters. The endpoint received request respond to the request by sending a RESULT message.

## Notification

A endpoint inform what methods they have by sending NOTIFICATION message to the other endpoint.

## Verification Level

Verification level indicates how the generated data is reliable.

### Individual Comment

Content generated from individual comments on the web, which may vary in reliability and should be verified for accuracy.

### Official Pronouncement

Content generated from authoritative sources, such as government reports or officially published information, which carries a higher level of reliability.

### Remote Resource

A resouce that is served from a remote server, such as API responce.

### Local Resource

A resource that is located within a local environment, such as a database or file system, providing content that is directly accessible by the AI agent.

## Protocol Architecture

# MCP Endpoints Interactions

## MCP Messages

MCP messages are JSON-RPC 2.0 style.

### REQUEST Structure

~~~text
REQUEST {
  id: Request ID (i),
  method: Method Name (b),
  parameters: [
    {
      id: Parameter ID (i),
      value: Parameter Value (b),
    }
  ]
}
~~~

### RESULT Structure

~~~text
RESULT {
  id: Request ID (i),
  [key: Responce Key (b)]: Responce Value (b),
}
~~~

### ERROR Structure

~~~text
ERROR {
  code: Error Code (i),
  reason: Reason (b),
  data: Data (b),
}

### NOTIFICATION Structure
~~~text
NOTIFICATION {
  id: Notification ID (i),
  method: Method Name (b),
  arguments: [
    {
      id: Argument ID (i),
      type: Argument Type (i),
    }
  ]
}
~~~

### RESOURCE

### TOOL

### PROMPT Structure

~~~text
PROMPT {
  name: Prompt Name (b),
  parameters?: [
    {
      id: Parameter ID (i),
      name: Parameter Name (b),
      required: Required (i),
    }...
  ]
}
~~~

### Concept Mapping

- "prompts/list" endpoint -> A Track named "prompts"

## Transport Mechanisms

### Set up

A session is the MOQT session and is established by a client dialing to a server.
Any additional information required to be exchanged when set up SHOULD be sent as an extention of the MOQ set up messages.

### Announce

Endpoints can know what resource they can access using MOQT announce negotiation.
This negotiation starts with a subscriber let a publisher know what resources they are interested in and then the publisher respond any announcement.
The server announce ...

### Subscribe

Reserved Tracks

### Fetch

### Terminate

# Implementation Guidelines

## Best Practices

## Performance Considerations

# IANA Considerations

# Security Considerations

# References

## Normative References

## Informative References

# Acknowledgments

--- back