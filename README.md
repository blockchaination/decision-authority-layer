# Decision Authority Layer (DAL)

The Decision Authority Layer (DAL) is an open specification that defines how decision authority is declared, constrained, and audited in AI-assisted systems.

DAL addresses the question: *Who or what has the authority to make a decision, under what constraints, and how is that authority verified?*

## What DAL Is

DAL is a formal specification for:

- **Declaring decision authority** : identifying which agent (human, AI, or hybrid) holds authority for a given decision
- **Constraining authority** : defining boundaries, prerequisites, and limitations on decision-making power
- **Auditing authority** : providing mechanisms to verify that decisions were made within authorized scope

DAL operates at the structural level, concerned with governance and accountability in systems where AI agents participate in decision-making processes.

## What DAL Is Not

DAL does not address:

- **Decision quality** : evaluating whether a decision is correct, optimal, or effective
- **Ethics or values** : determining what decisions should be made from a moral perspective
- **AI alignment** : ensuring AI systems pursue intended goals or human values
- **Model behavior** : controlling or improving how AI models generate outputs

DAL is a governance framework, not a quality assurance or alignment mechanism.

## Specification

The current specification is version 0.1 and is under active development.

- [Specification (v0.1)](./spec/)

## Participate

DAL is an open standard. Contributions, feedback, and discussion are welcome.

- [Discussions](https://github.com/blockchaination/decision-authority-layer/discussions) : General discussion, proposals, and questions
- [Issues](https://github.com/blockchaination/decision-authority-layer/issues) : Bug reports and specification improvements

## License

This specification is released under the [Apache License 2.0](./LICENSE).
