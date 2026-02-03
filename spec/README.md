# Decision Authority Layer (DAL) v0.1 Specification

## Abstract

In systems where artificial intelligence agents participate in decision-making processes, accountability structures become ambiguous when authority to act is not formally declared. The Decision Authority Layer (DAL) specifies a structural framework for explicitly declaring which agents—human, automated, or hybrid—hold authority to make specific decisions, under what constraints that authority operates, and through what mechanisms such authority can be verified.

DAL defines a set of core components: (1) declaration of decision authority, identifying the agent or agents authorized to execute a decision; (2) constraints on authority, establishing boundaries, prerequisites, and conditions under which authority is valid; and (3) auditability of authority, providing verifiable records that decisions were made by authorized agents within defined limits.

DAL operates at the governance layer. It addresses the structural question of who or what is authorized to decide, not whether decisions are correct, ethical, or aligned with specific values. DAL does not evaluate decision quality, encode moral principles, ensure AI alignment, or control model behavior. It exists to make authority explicit, inspectable, and subject to formal verification.

This specification is intended for systems where decision authority must be auditable, including regulated environments, multi-agent systems, and human-AI collaborative workflows.

## Motivation

When automated systems participate in decision-making processes, the question of who holds authority to act becomes critical for accountability. In traditional systems, authority is inherent in organizational structure or explicitly delegated through documented procedures. When automation is introduced, this clarity often erodes.

Systems that incorporate automated decision-making frequently exhibit implicit authority structures. A function executes, a threshold is crossed, a recommendation is accepted, and an action occurs. The chain of authorization is present in code, configuration, or workflow logic, but it is not declared in a form that supports inspection, constraint, or audit. Responsibility for outcomes becomes diffuse because the locus of authority is not explicit.

Existing approaches address related but distinct problems. Model alignment focuses on ensuring that systems behave according to intended objectives. This addresses what a system does, not who authorized it to act. Explainability techniques provide reasoning for how a decision was reached. This clarifies mechanism, not authority. Logging records actions after they occur. Post-hoc review analyzes decisions retrospectively. Neither establishes authority prospectively or prevents unauthorized actions.

None of these methods answer the foundational question: was this agent authorized to make this decision under these conditions? Without explicit authority declarations, accountability structures rely on inference, reconstruction, or custom implementations that vary across systems. Auditors, regulators, and operators cannot determine whether decisions were made within authorized scope without reverse-engineering system internals.

The gap is structural. Authority must be declared before decisions are made, constrained by conditions that limit scope, and subject to verification that actions fall within authorized boundaries. This requires a formal mechanism independent of implementation details. Such a mechanism must support explicit declaration of which agents hold authority, under what conditions authority applies, and how authority can be escalated.

DAL addresses this gap by formalizing decision authority as a distinct layer in system design.

## Non-Goals

DAL does not evaluate decision quality or correctness. It does not assess whether a decision is right, wrong, optimal, or suboptimal. Quality evaluation is outside the scope of this specification.

DAL does not encode ethical, moral, or normative judgments. It provides no framework for determining what should be decided, only who is authorized to decide. Value systems, ethical principles, and normative constraints are not addressed.

DAL does not perform model alignment, training, or inference. It does not modify, configure, or control how models generate outputs. Model behavior is not within scope.

DAL does not replace or override human responsibility. Declaration of authority does not absolve individuals or organizations of accountability for outcomes. Legal, professional, and organizational responsibilities remain unchanged.

DAL does not guarantee safety, compliance, or optimal outcomes. Proper use of DAL does not ensure that decisions will be safe, compliant with regulations, or effective. Separate verification mechanisms are required for these properties.

DAL does not define how decisions should be made. It does not prescribe decision-making processes, methodologies, or criteria. Process design remains the responsibility of implementers.

DAL does not provide enforcement, automation, or execution mechanisms. It specifies what should be declared, not how declarations are enforced or decisions are executed. Implementation of enforcement is left to adopters.

## Core Concepts

### Decision Unit

The Decision Unit is the fundamental atomic element of the Decision Authority Layer. It is defined as the smallest indivisible action within a system that produces a change in system state or real-world state.

A Decision Unit is the specific locus where authority is exercised. It is the unit to which authority is assigned and against which accountability is audited.

A Decision Unit MUST satisfy the following properties:

1.  **Atomicity**: It cannot be subdivided into smaller decision components.
2.  **Effect**: Its execution results in a modification of system state or real-world state.
3.  **Identifiability**: It must be uniquely addressable and distinguishable from other units.
4.  **Accountability**: It serves as the anchor point for authority assignment and audit records.

### Authority Holder

An Authority Holder is an identifiable actor that is permitted to exercise authority over one or more Decision Units. An Authority Holder may be a human, an organization, or a system component.

Authority Holders do not make decisions by default. They hold permission to decide. Authority must be explicitly assigned. It is never implied by role, function, or proximity to a Decision Unit.

Authority Holders are accountable for decisions executed under their declared authority.

An Authority Holder MUST satisfy the following properties:

1.  **Identifiability**: It must be uniquely addressable within the system.
2.  **Explicit Assignment**: Authority over Decision Units must be declared, not inferred.
3.  **Accountability**: It bears responsibility for decisions made under its authority.

### Authority Scope

Authority Scope is the bounded set of conditions under which an Authority Holder may exercise authority over Decision Units. Scope constrains authority by defining the conditions that must be satisfied for authority to apply.

Authority exercised outside declared scope is unauthorized. Scope must be explicit and inspectable. It applies prospectively, establishing validity before a decision is executed.

Authority Scope MUST satisfy the following properties:

1.  **Explicitness**: Boundaries of authority must be declared in a form that permits inspection.
2.  **Constraint**: It must specify the conditions under which authority is valid.
3.  **Prospectivity**: It governs future actions, not past events.

### Escalation Path

An Escalation Path is the declared sequence through which authority may be transferred when an Authority Holder lacks sufficient scope to act on a Decision Unit.

Escalation preserves continuity of authority. It does not bypass authority constraints. Escalation paths must be explicit and inspectable. Absence of an applicable escalation path results in non-action.

An Escalation Path MUST satisfy the following properties:

1.  **Explicitness**: The sequence of authority transfer must be declared in a form that permits inspection.
2.  **Continuity**: It must preserve an unbroken chain of authority from origin to resolution.
3.  **Constraint Preservation**: It must not permit authority to be exercised outside declared scope.
4.  **Determinacy**: Absence of an applicable path must result in a defined non-action state.

### Accountability Record

An Accountability Record is a durable record that captures exercised authority over a Decision Unit. It links the Decision Unit, the Authority Holder, the Authority Scope under which authority was exercised, and the Escalation Path if applicable.

Records are generated at execution time or immediately after. Records must be inspectable. Absence of an Accountability Record invalidates the decision for audit purposes.

An Accountability Record MUST satisfy the following properties:

1.  **Durability**: It must persist in a form that survives the execution context.
2.  **Completeness**: It must reference the Decision Unit, Authority Holder, and applicable Authority Scope.
3.  **Traceability**: It must include the Escalation Path if escalation occurred.
4.  **Inspectability**: It must be accessible for review and audit.
5.  **Timeliness**: It must be generated at or immediately following execution.

## Conformance Requirements

### Conformance Model

A system either conforms to this specification or does not conform. Partial adoption or informal alignment does not constitute conformance. Conformance is assessed at the system boundary.

### Minimum Conformance Requirements

A conforming system MUST satisfy the following requirements:

1.  All Decision Units MUST be explicitly identifiable within the system.
2.  Each Decision Unit MUST have at least one Authority Holder assigned.
3.  Authority Scope MUST be declared for each Authority Holder.
4.  Escalation Paths MUST be declared where authority transfer is permitted.
5.  An Accountability Record MUST be generated for each executed Decision Unit.
6.  Decisions executed without valid authority or without corresponding Accountability Records MUST be treated as non-conformant.

## Normative Rules

This specification uses normative language to indicate requirements for conformance. The key words MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, and OPTIONAL are to be interpreted as described in RFC 2119.

Statements containing these terms define conditions that a conforming system is required or permitted to satisfy. Failure to satisfy a MUST or MUST NOT requirement results in non-conformance. SHOULD and SHOULD NOT indicate recommendations that may be deviated from with justification. MAY indicates optional behavior.

Text that does not contain normative keywords is non-normative. Non-normative text provides context, explanation, or rationale. It does not establish requirements and does not affect conformance assessment.

## Minimal Compliance

Minimal Compliance defines the minimum declarations an implementation must expose to support DAL conformance. It establishes what must be declared, not how declarations are stored, transmitted, or enforced.

A minimally compliant implementation MUST declare the following:

1.  **Decision Units**: The set of Decision Units within the system must be enumerated and identifiable.
2.  **Authority Holders**: The Authority Holder or Holders assigned to each Decision Unit must be declared.
3.  **Authority Scope**: The Authority Scope applicable to each Authority Holder must be declared.
4.  **Escalation Paths**: Any Escalation Paths associated with each Decision Unit must be declared where authority transfer is permitted.

These declarations MUST be accessible for inspection. Inspection means that an authorized party can retrieve and examine the declarations without requiring access to implementation internals.

Minimal Compliance does not require enforcement mechanisms, runtime automation, or active prevention of unauthorized decisions. These capabilities may be implemented but are not required for conformance.

## Failure Modes & Misuse

DAL is a structural specification for declaring decision authority. It is not a complete governance system. Misunderstanding its scope or capabilities can lead to ineffective or harmful implementations.

### Declaration Without Enforcement

DAL requires that authority be declared. It does not require that declarations be enforced. A system may declare Authority Scope for all Decision Units and still permit unauthorized decisions to execute. Declaration alone provides auditability, not prevention. Implementers who assume that DAL declarations automatically prevent unauthorized actions have misunderstood the specification.

Enforcement mechanisms are outside the scope of DAL. Systems that require active prevention of unauthorized decisions must implement enforcement separately.

### Substitution for Decision Quality

DAL declares who is authorized to decide. It does not evaluate whether decisions are correct, optimal, or appropriate. Implementers who treat DAL conformance as validation of decision quality have misapplied the specification.

A system may be fully DAL-conformant and still produce harmful, incorrect, or suboptimal outcomes. DAL addresses authority, not correctness.

### Displacement of Human Accountability

DAL formalizes authority declarations. It does not transfer or reduce human responsibility for outcomes. Implementers who treat DAL as a mechanism for absolving individuals or organizations of accountability have misunderstood its purpose.

Declaration of authority does not constitute delegation of responsibility. Legal, professional, and organizational accountability structures remain in effect regardless of DAL conformance.

### Completeness Illusion

DAL specifies minimum requirements for authority declaration. Conformance does not guarantee that all relevant authority has been declared, that scope constraints are sufficient, or that escalation paths are comprehensive. Implementers who assume that DAL conformance ensures complete governance have overestimated the specification's scope.

DAL establishes a baseline for explicitness. It does not ensure that declarations are thorough, well-designed, or adequate for a given context.

### Ethical or Normative Substitution

DAL provides no framework for determining what should be decided or how decisions should align with values, ethics, or principles. Implementers who treat DAL as a substitute for ethical governance, value alignment, or normative constraint systems have misapplied the specification.

DAL is value-neutral by design. Ethical and normative considerations must be addressed through separate mechanisms.

## Open Questions

This section identifies design areas that remain unresolved in v0.1. These are not implementation details left to adopters. They are structural questions that require specification-level resolution in future versions.

### Cross-System Authority Composition

When Decision Units span multiple systems, it is unclear how Authority Scope declarations should compose. If System A declares authority over a Decision Unit and System B also declares authority over the same unit, DAL v0.1 provides no mechanism for resolving conflicts, establishing precedence, or validating consistency.

This specification does not address federated or distributed authority models.

### Authority Scope Modification

DAL requires that Authority Scope be declared. It does not specify whether scope can be modified after initial declaration, under what conditions modification is valid, or how modifications affect in-flight decisions.

Dynamic scope adjustment may be necessary in adaptive systems, but the semantics of scope modification are not defined.

### Temporal Constraints on Authority

Authority may be time-bounded in practice. DAL does not provide a normative structure for expressing temporal constraints on Authority Scope, such as expiration, scheduled activation, or time-limited delegation.

Whether temporal constraints should be specified within Authority Scope or as a separate construct is unresolved.

### Authority Revocation Semantics

DAL permits Authority Holders to be assigned to Decision Units. It does not define how authority is revoked, whether revocation is retroactive, or how revocation affects decisions made under previously valid authority.

Revocation semantics are undefined.

### Conflict Resolution Between Authority Holders

When multiple Authority Holders are assigned to a Decision Unit, DAL does not specify how conflicts are resolved if scope constraints permit multiple valid decisions. Whether conflicts should be resolved through precedence, consensus, or escalation is unresolved.

### Granularity Boundaries for Decision Units

DAL defines Decision Units as atomic and indivisible. It does not provide criteria for determining appropriate granularity. Whether a sequence of actions constitutes one Decision Unit or multiple units is left to implementers, which may result in inconsistent decomposition across systems.

### Accountability Record Retention and Access

DAL requires Accountability Records to be durable and inspectable. It does not specify retention duration, access control policies, or deletion conditions. Long-term record management is outside the scope of v0.1.

## Versioning

### Version Numbering

This specification uses semantic versioning. Version numbers are structured as MAJOR.MINOR. Changes to MAJOR indicate backwards-incompatible modifications to conformance requirements. Changes to MINOR indicate backwards-compatible additions or clarifications.

This document specifies DAL v0.1. The 0.x series indicates that the specification is under active development and has not achieved stability. Breaking changes may occur between 0.x versions without incrementing MAJOR.

### Stability Guarantee

DAL v0.x provides no stability guarantee. Conformance requirements, core concepts, and normative rules may change in incompatible ways between minor versions. Implementations that conform to v0.1 may not conform to v0.2.

DAL v1.0 will mark the first stable release. After v1.0, MAJOR version increments will indicate breaking changes. MINOR version increments will indicate backwards-compatible changes.

### Deprecation Policy

DAL v0.x does not support deprecation. Features or requirements may be removed without prior notice. After v1.0, deprecated features will be marked in the specification and retained for at least one MAJOR version before removal.

### Extension and Profiles

Implementations MAY extend DAL by adding capabilities beyond the minimum conformance requirements. Extensions MUST NOT conflict with normative requirements. Extensions MUST be clearly identified as non-normative additions.

Future versions of DAL may define conformance profiles that specify subsets or extensions of the core specification for particular use cases. DAL v0.1 does not define profiles.

### Conformance Across Versions

A system that conforms to DAL v0.x does not automatically conform to later versions. Conformance must be re-assessed when migrating between versions. After v1.0, systems conforming to v1.x will remain conformant under v1.y where y > x, but not necessarily under v2.0.

### Change Process

DAL v0.x is maintained through open development. Proposed changes are evaluated based on alignment with the specification's scope, compatibility with existing conformance requirements, and clarity of normative language. The change process will be formalized before v1.0.
