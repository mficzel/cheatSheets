=======================  =======================================================================================================================================================================================================================
Domain Driven Design (terms by wikipedia)
================================================================================================================================================================================================================================================
Domain                   A sphere of knowledge, in! uence, or activity. The subject area to which the user applies a program is the domain of the software.
Model                    A system of abstractions that describes selected aspects of a domain and can be used to solve problems related to that domain.
Ubiquitous Language(UL)  A language structured around the domain model and used by all team members to connect all the activities of the team with the software. The words of the UL are used throughout all artefacts.
Context                  The setting in which a word or statement appears that determines its meaning.
Entity                   An object that is not defined by its attributes, but rather by a thread of continuity and its identity. Derives from class Tx_Extbase_DomainObject_AbstractEntity
Value Object (VO)        An object that contains attributes but has no conceptual identity. They should be treated as immutable. Derives from class Tx_Extbase_DomainObject_AbstractValueObject
Aggregate                A collection of objects that are bound together by a root entity, otherwise known as an aggregate root.
Aggregate root           The aggregrate root guarantees the consistency of changes being made within the aggregate by forbidding external objects from holding references to its members.
Service                  When an operation does not conceptually belong to any object. Following the natural contours of the problem, you can implement these operations in services.
Repository               Methods for retrieving domain objects should delegate to a specialized Repository object such that alternative storage implementations may be easily interchanged. Derives from class Tx_Extbase_Persistence_Repository
=======================  =======================================================================================================================================================================================================================
