# HCP-0004
# Node Identity

Version: 0.1 (Draft)

Status: Draft

Depends on:

- Humanitarian Connection Protocol Specification v0.1
- HCP-0002 HCP Node

---

# 1. Purpose

This specification defines how an HCP Node obtains and maintains its identity within the Humanitarian Connection Protocol.

Node Identity enables secure participation in the network while preserving the decentralized nature of HCP.

The identity of a node is independent of the software clients that interact with it.

---

# 2. Definition

A Node Identity is the unique cryptographic identity assigned to an HCP Node.

It allows other nodes to recognize the origin of Humanitarian Records and establish trusted communication.

The identity belongs to the node itself, not to its operators.

---

# 3. Design Principles

Node Identity SHALL satisfy the following principles:

- Unique
- Persistent
- Cryptographically verifiable
- Decentralization-friendly
- Independent from any specific identity provider
- Compatible with future trust models

---

# 4. Node Registration

An HCP Node MAY be registered through the Human Connection Network Foundation.

The registration process exists to:

- verify that the applicant represents a real individual or organization;
- generate an initial Node Identity;
- issue a Node UUID;
- generate the node's cryptographic key pair;
- optionally publish the node in the public HCP Node Directory.

Registration is a service provided by the Foundation.

It is not a requirement for the HCP protocol itself.

---

# 5. Identity Providers

During node registration, applicants MAY authenticate using one or more Identity Providers (IdPs).

Examples include:

- Google
- Microsoft
- Apple
- GitHub
- Government Digital Identity Systems
- Universities
- Hospitals
- Enterprise Identity Providers

Identity Providers are used only during the registration process.

They do not participate in the operation of the HCP network.

---

# 6. Node Identity Components

Every Node Identity SHOULD contain:

- Node UUID
- Public Key
- Private Key (stored only by the node)
- Creation Timestamp
- Protocol Version
- Node Category

Future specifications MAY define additional attributes.

---

# 7. Node Categories

Nodes MAY declare one or more categories.

Examples include:

- Foundation Node
- Institutional Node
- Government Node
- Healthcare Node
- Community Node
- Research Node
- Emergency Node

Node categories provide contextual information.

They do not grant additional authority within the protocol.

---

# 8. Node Operators

A node MAY have one or more operators.

Operators administer the node.

Operators do not own the node identity.

Changes in node operators SHALL NOT modify the Node UUID.

Operator management is implementation-specific.

---

# 9. Public Node Directory

The Human Connection Network Foundation MAY maintain a public directory of registered nodes.

Publication in the directory is optional.

Nodes MAY operate privately without appearing in the directory.

The directory is intended to facilitate discovery and collaboration.

It is not required for protocol interoperability.

---

# 10. Security

Every node SHALL protect its private key.

Private keys SHALL NEVER be transmitted to other nodes.

Future specifications define:

- key rotation;
- certificate renewal;
- identity revocation;
- compromised node recovery.

---

# 11. Compliance

Any implementation claiming compatibility with HCP SHOULD possess a stable Node Identity.

Implementations participating in public synchronization SHOULD expose their public key.

---

# 12. Philosophy

Identity exists to identify nodes, not people.

Humanitarian Records are created by nodes.

Nodes are administered by people or organizations.

By separating these concepts, HCP maintains a clear distinction between infrastructure, operators and humanitarian information.

---

**End of HCP-0004**
