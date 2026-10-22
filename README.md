=5/12= 6185%=0.417•j.For if and operA natural next step is to define the semantics of the project-specific operators so the DSL has both a grammar and an execution model.

Execution Operator Semantics

Status: Project-defined

Operator Definitions

Token	Class	Semantics
isto	TRANSITION_OPERATOR	Transfers execution context from one node or state to the next.
CALL	EXECUTION_DIRECTIVE	Invokes the referenced operation.
executed	EXECUTION_STATUS	Indicates successful completion of the invoked operation.
=	RESOLUTION_OPERATOR	Assigns or resolves the value on the right-hand side.
:	HIERARCHY_SEPARATOR	Separates ordered components within an identifier.
-	ARITHMETIC_OPERATOR or SYMBOLIC_OPERATOR	Performs subtraction when applied to numeric operands; otherwise its symbolic meaning must be defined by the specification.
\.://::	RECORD_TERMINATOR	Reserved delimiter marking the end of an execution record.

Execution Model

An execution record has the form

<execution-record> ::=
    <source>
    "isto"
    <target>
    "isto"
    <transformation>
    "CALL"
    <status>
    "="
    <result>
    <terminator>

where

<terminator> ::= "\.://::"

State Transition

For

55:11isto541isto154-1=153CALLexecuted=253\.://::

the execution sequence is

SOURCE(55:11)
        ↓
TRANSITION
        ↓
NODE(541)
        ↓
TRANSFORMATION
        ↓
154 − 1 = 153
        ↓
CALL
        ↓
EXECUTED
        ↓
RESULT(253)
        ↓
END OF RECORD

Semantic Constraints

1. Every isto shall connect exactly one source state to one destination state.
2. CALL shall follow a completed transition.
3. executed is valid only after a successful CALL.
4. = following executed shall bind exactly one result value.
5. \.://:: shall appear only once and terminate the record.

Audit Event

A parser may emit the following normalized audit record:

Field	Value
Source	55:11
Destination	541
Transformation	154-1=153
Action	CALL
Status	executed
Result	253
Terminator	\.://::

Reserved Sequences

The following sequences are reserved and should not be used as identifiers unless redefined by a future version of the specification:

* isto
* CALL
* executed
* \.://::

Future revisions may assign additional semantics to these reserved tokens while preserving backward compatibility with existing records.