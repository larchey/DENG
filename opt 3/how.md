here is a step-by-step breakdown of the AI framework's functionality, from data ingestion to drift detection.

The proposed solution operates in a three-stage, interconnected flow, where two distinct AI models—a Natural Language Processing (NLP) model and a Graph Neural Network (GNN)—work in parallel before their outputs are reconciled by a final, novel algorithm.

Stage 1: The Intent (NLP Model)

    Input: The unstructured "approved changes" document is fed into the system. This document contains human-readable text describing a planned modification to a RHEL endpoint, such as "John Doe will install Nginx."

    Processing: An NLP model is used to semantically analyze the document, a technique that allows a machine to understand the meaning of human language. The NLP model identifies key entities and relationships within the text, such as who is making the change (   

user: John Doe), what the intended action is (action: install), and which system components are involved (app: Nginx).  

    Output: This unstructured text is transformed into a formal, machine-readable "intent graph." This graph represents the approved plan for a system change and serves as the official "ground truth" for what is allowed to happen on the RHEL endpoint.

Stage 2: The Reality (GNN Model)

    Input: Real-time data from a large number of RHEL endpoints is collected by Elastic Agents, which are configured to ingest auditd logs. These logs capture a comprehensive record of system events, including file modifications, process executions, and user activity.   

Processing: This continuous stream of system data is fed into a Graph Neural Network (GNN). The GNN is specifically designed to model the interconnected relationships of system components. It dynamically builds a graph where nodes represent entities like users, processes, and files, and edges represent the relationships between them (e.g., a user  

executes a process).  

Output: The GNN produces a continuously updated "actual state graph" that reflects the current, live state of the RHEL endpoint. By modeling the system this way, the GNN can detect subtle patterns and deviations that would be difficult to spot with traditional methods.  

Stage 3: The Reconciliation (Novel Algorithm)

    The Core of the Thesis: This is the critical, unique step that differentiates the proposed solution. The system's novel algorithm performs a cross-modal comparison by reconciling the "intent graph" (the plan) with the "actual state graph" (the reality).   

Functionality: The algorithm formally compares the two graphs to determine if an observed change on the system is aligned with an approved, documented change. For example, if the GNN detects that "John Doe installed Nginx," it references the "intent graph." If it finds a corresponding approved change, the system classifies the action as a valid modification rather than a security threat.

Output: Any change that occurs on the "actual state graph" that does not have a corresponding, approved entry in the "intent graph" is formally identified and scored as a genuine instance of configuration drift. This distinction allows the system to differentiate between authorized changes and genuine, malicious or unauthorized deviations.