=======================  =======================================================================================================================================================================================================================
Domain Driven Design (terms by wikipedia)
================================================================================================================================================================================================================================================
Domain                   A sphere of knowledge, in! uence, or activity. The subject area to which the user applies a program is the domain of the software.
Model                    A system of abstractions that describes selected aspects of a domain and can be used to solve problems related to that domain.
Ubiquitous Language(UL)  A language structured around the domain model and used by all team members to connect all the activities of the team with the software. The words of the UL are used throughout all artefacts.
Context                  The setting in which a word or statement appears that determines its meaning.
Entity                   An object that is not defined by its attributes, but rather by a thread of continuity and its identity. Derives from class ``Tx_Extbase_DomainObject_AbstractEntity``
Value Object (VO)        An object that contains attributes but has no conceptual identity. They should be treated as immutable. Derives from class ``Tx_Extbase_DomainObject_AbstractValueObject``
Aggregate                A collection of objects that are bound together by a root entity, otherwise known as an aggregate root.
Aggregate root           The aggregrate root guarantees the consistency of changes being made within the aggregate by forbidding external objects from holding references to its members.
Service                  When an operation does not conceptually belong to any object. Following the natural contours of the problem, you can implement these operations in services.
Repository               Methods for retrieving domain objects should delegate to a specialized Repository object such that alternative storage implementations may be easily interchanged. Derives from class ``Tx_Extbase_Persistence_Repository``
=======================  =======================================================================================================================================================================================================================

=======================   =====================================
Naming Conventions
===============================================================
Classes                   UpperCamelCase
Methods & Variables       lowerCamelCase
General class naming      Tx_[ExtensionName]_[Path].php

                          - [ExtensionName] is extension_key without _ and in UpperCamelCase
                          - [Path] is inside Classes directory of the extension, change / with _

                          e.g.:

                          Class-Name: Tx_BlogExample_Domain_Model_Post

                          Path & Filename: typo3conf/ext/blog_example/Classes/Domain/Model/Post.php or

                          Class-Name: Tx_Extbase_MVC_Controller_ActionController

                          Path & Filename: typo3/sysext/extbase/Classes/MVC/Controller/ActionController.php
Interfaces                Class name ends in „Interface“, e.g. Tx_Extbase_MVC_RequestInterface
Abstact classes           beginning of last class name part is „Abstract“
                          e.g. Tx_Extbase_MVC_Controller_AbstractController
                          Domain model entity: ... extends Tx_Extbase_DomainObject_AbstractEntity
                          Domain model value object: ... extends Tx_Extbase_DomainObject_AbstractValueObject
=======================   =====================================

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

=======================================================================  ===================================
**Folder structure inside extension dir typo3conf/ext/[extension_key]/**
============================================================================================================
ext_autoload.php                                                         Mapping classname to classfile location
ext_emconf.php                                                           Extension manager configuration
ext_icon.gif                                                             Extension icon
ext_localconf.php                                                        Frontend configuration
ext_tables.php                                                           SQL statements for the databse structure
ext_tables.sql                                                           ExtensionBuilder configuration
-----------------------------------------------------------------------  -----------------------------------
**Classes/**                                                             **All PHP classes reside here**
-----------------------------------------------------------------------  -----------------------------------
Classes/Controller/                                                      Controller classes
Classes/Controller/[DomainObjectName]Controller.php                      Controller of model [DomainObjectName] (rec.)
Classes/Domain/                                                          Domain specific classes
Classes/Domain/Model/                                                    Model classes
Classes/Domain/Model/[DomainObjectName].php                              Specific model class for [DomainObjectName]
Classes/Domain/Repository/                                               Repository classes
Classes/Domain/Repository/[DomainObjectName]Repository.php               Repository of model [DomainObjectName]
Classes/Domain/Validator/                                                Validator classes
Classes/Domain/Validator/[DomainObjectName]Validator.php                 Validator of model [DomainObjectName]
Service                                                                  Service classes
Utillity                                                                 Utillity classes (just helper classes)
Classes/ViewHelpers/                                                     Individual fluid view helpers reside here
Classes/ViewHelpers/[VHName]ViewHelper.php                               View helper with name VHName
-----------------------------------------------------------------------  -----------------------------------
**Configuration/**                                                       **All configuration (structure is a suggestion)**
-----------------------------------------------------------------------  -----------------------------------
Configuration/TCA/                                                       Table configuration array (TCA) Files e.g.: [DomainObjectName].php
Configuration/FlexForms/                                                 Flexforms used for backend forms
Configuration/TypoScript/                                                TypoScript constants and setup (e.g. constants.txt and setup.txt)
-----------------------------------------------------------------------  -----------------------------------
**Documentation/**                                                       **All documentation reside here**
-----------------------------------------------------------------------  -----------------------------------
Documentation/Manual/                                                    Extension manual, subfolder [format]/[lang]/
-----------------------------------------------------------------------  -----------------------------------
**Resources/**                                                           **All resources reside here**
-----------------------------------------------------------------------  -----------------------------------
Resources/Private/                                                       Private resources
Resources/Private/Backend/                                               Resources used by backend modules
Resources/Private/Backend/Layouts/                                       Layout files for backend modules
Resources/Private/Backend/Templates/                                     Template files for backend modules
Resources/Private/Backend/Templates/[ControllerName]/                    All templates of a specific controller (BE)
Resources/Private/Backend/Templates/[ControllerName]/[action].[format]   Template of [action] from [Controller] (BE)
Resources/Private/Language/                                              Language files for l10n
Resources/Private/Language/locallang.xml                                 Main language file - use key w. translate viewhelper
Resources/Private/Layouts/                                               Layout files for frontend plugins
Resources/Private/Partials/                                              Partials files for frontend plugins
Resources/Private/Templates/                                             Template files for frontend plugins
Resources/Private/Templates/[Controller]/                                All templates of a specific controller (FE)
Resources/Private/Templates/[Controller]/[Action].[format]               Template of [Action] from [Controller] (FE)
Resources/Public/                                                        Additional resources (own dirs if needed, like „Icons“, ...)
-----------------------------------------------------------------------  -----------------------------------
**Tests/**                                                               **All tests reside here**
-----------------------------------------------------------------------  -----------------------------------
Tests/Unit/                                                              Unit Tests
=======================================================================  ===================================

