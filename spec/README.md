# Decision Authority Layer (DAL) v0.1 Specification

## Abstract

In systems where artificial intelligence agents participate in decision-making processes, accountability structures become ambiguous when authority to act is not formally declared. The Decision Authority Layer (DAL) specifies a structural framework for explicitly declaring which agents—human, automated, or hybrid—hold authority to make specific decisions, under what constraints that authority operates, and through what mechanisms such authority can be verified.

DAL defines three core components: (1) declaration of decision authority, identifying the agent or agents authorized to execute a decision; (2) constraints on authority, establishing boundaries, prerequisites, and conditions under which authority is valid; and (3) auditability of authority, providing verifiable records that decisions were made by authorized agents within defined limits.

DAL operates at the governance layer. It addresses the structural question of who or what is authorized to decide, not whether decisions are correct, ethical, or aligned with specific values. DAL does not evaluate decision quality, encode moral principles, ensure AI alignment, or control model behavior. It exists to make authority explicit, inspectable, and subject to formal verification.

This specification is intended for systems where decision authority must be auditable, including regulated environments, multi-agent systems, and human-AI collaborative workflows.

## Motivation

When automated systems participate in decision-making processes, the question of who holds authority to act becomes critical for accountability. In traditional systems, authority is inherent in organizational structure or explicitly delegated through documented procedures. When automation is introduced, this clarity often erodes.

Systems that incorporate automated decision-making frequently exhibit implicit authority structures. A function executes, a threshold is crossed, a recommendation is accepted, and an action occurs. The chain of authorization is present in code, configuration, or workflow logic, but it is not declared in a form that supports inspection, constraint, or audit. Responsibility for outcomes becomes diffuse because the locus of authority is not explicit.

Existing approaches address related but distinct problems. Model alignment focuses on ensuring that systems behave according to intended objectives. This addresses what a system does, not who authorized it to act. Explainability techniques provide reasoning for how a decision was reached. This clarifies mechanism, not authority. Logging records actions after they occur. Post-hoc review analyzes decisions retrospectively. Neither establishes authority prospectively or prevents unauthorized actions.

None of these methods answer the foundational question: was this agent authorized to make this decision under these conditions? Without explicit authority declarations, accountability structures rely on inference, reconstruction, or custom implementations that vary across systems. Auditors, regulators, and operators cannot determine whether decisions were made within authorized scope without reverse-engineering system internals.

The gap is structural. Authority must be declared before decisions are made, constrained by conditions that limit scope, and subject to verification that actions fall within authorized boundaries. This requires a formal mechanism independent of implementation details. Such a mechanism must support explicit declaration of which agents hold authority, under what conditions authority applies, and how authority can be escalated or revoked.

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

The Decision Unit is the fundamental atomic element of the Decision Authority Layer. It is defined as the smallest indivisible action within a system that produces a state change or an external effect.

A Decision Unit is the specific locus where authority is exercised. It is the entity to which authority is assigned and against which accountability is audited.

A Decision Unit MUST satisfy the following properties:

1.  **Atomicity**: It cannot be subdivided into smaller decision components.
2.  **Effect**: Its execution results in a modification of system state or real-world state.
3.  **Identifiability**: It must be uniquely addressable and distinguishable from other units.
4.  **Accountability**: It serves as the anchor point for authority assignment and audit records.

## Normative Rules
(Uses MUST / SHOULD / MAY language)

## Minimal Compliance
(What an implementation must declare)

## Failure Modes & Misuse
(How DAL can be misapplied)

## Open Questions
(Explicitly unresolved areas)

## Versioning
(How the standard evolves)
