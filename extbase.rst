=======================  =======================================================================================================================================================================================================================
Domain Driven Design (terms by wikipedia)
================================================================================================================================================================================================================================================
Domain                   A sphere of knowledge, in! uence, or activity. The subject area to which the user applies a program is the domain of the software.
Model                    A system of abstractions that describes selected aspects of a domain and can be used to solve problems related to that domain.
Ubiquitous Language(UL)  A language structured around the domain model and used by all team members to connect all the activities of the team with the software. The words of the UL are used throughout all artefacts.
Context                  The setting in which a word or statement appears that determines its meaning.
Entity                   An object that is not defined by its attributes, but rather by a thread of continuity and its identity. Derives from class `Tx_Extbase_DomainObject_AbstractEntity``
Value Object (VO)        An object that contains attributes but has no conceptual identity. They should be treated as immutable. Derives from class ``Tx_Extbase_DomainObject_AbstractValueObject``
Aggregate                A collection of objects that are bound together by a root entity, otherwise known as an aggregate root.
Aggregate root           The aggregrate root guarantees the consistency of changes being made within the aggregate by forbidding external objects from holding references to its members.
Service                  When an operation does not conceptually belong to any object. Following the natural contours of the problem, you can implement these operations in services.
Repository               Methods for retrieving domain objects should delegate to a specialized Repository object such that alternative storage implementations may be easily interchanged. Derives from class Tx_Extbase_Persistence_Repository
=======================  =======================================================================================================================================================================================================================

+-----------------------------------------------------------------------------------------------------------------+
| Naming Conventions                                                                                              |
+=======================+=========================================================================================+
| Classes               | UpperCamelCase                                                                          |
+-----------------------+-----------------------------------------------------------------------------------------+
| Methods & Variables   | lowerCamelCase                                                                          |
+-----------------------+-----------------------------------------------------------------------------------------+
| General class naming  | Tx_[ExtensionName]_[Path].php                                                           |
|                       | - [ExtensionName] is extension_key without _ and in UpperCamelCase                      |
|                       | - [Path] is inside Classes directory of the extension, change / with _                  |
|                       | e.g.:                                                                                   |
|                       | Class-Name: Tx_BlogExample_Domain_Model_Post                                            |
|                       | Path & Filename: typo3conf/ext/blog_example/Classes/Domain/Model/Post.php or            |
|                       | Class-Name: Tx_Extbase_MVC_Controller_ActionController                                  |
|                       | Path & Filename: typo3/sysext/extbase/Classes/MVC/Controller/ActionController.php       |
+-----------------------+-----------------------------------------------------------------------------------------+
| Interfaces            | Class name ends in „Interface“, e.g. Tx_Extbase_MVC_RequestInterface                    |
+-----------------------+-----------------------------------------------------------------------------------------+
| Abstact classes       | beginning of last class name part is „Abstract“                                         |
|                       | e.g. Tx_Extbase_MVC_Controller_AbstractController                                       |
|                       | Domain model entity: ... extends Tx_Extbase_DomainObject_AbstractEntity                 |
|                       | Domain model value object: ... extends Tx_Extbase_DomainObject_AbstractValueObject      |
+-----------------------+-----------------------------------------------------------------------------------------+

=============================  ===================================
PHPDoc annotations
==================================================================
@param [Type] $var             Action: Parameter. $var validates to [Type]
@dontvalidate $var             Action: No validation for $var (needed for new und edit actions)
@var [Type]                    Model: Type of var in Domain Model - either simple type, class or ObjectStorage: Tx_Extbase_Persistence_ObjectStorage<Tx_[ExtensionName]_Domain_Model_[Model]> delivers methods: count(), attach(), attachAll(), detach(), detachAll(), contains(), ...
@validate [$var] [Validator]   Model & Action: Validation for $var. In model without $var.
@lazy                          Lazy loading in domain model (load child objects only when needed)
@cascade                       remove Delete child(s) if parent is removed
@dontverifyrequesthash         Disable request hash checking
@return [Type]                 Return value is of type [Type]
@api                           Declares that the following class/method is part of the official API
@deprecated                    Declares that the following class/method should not be used anymore
@scope                         Defines the type of the class. Possible values are prototype and singleton Not used in the moment: For singleton use ...implements t3lib_Singleton instead
=============================  ===================================
