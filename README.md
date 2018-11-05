# An analysis of structural interoperability in ISO 13606 based on typed lambda calculus

## abstract

> **ISO 13606** defines a standard specification for the exchange and integration of electronic health record (EHR) data with the goal of interoperability of EHR data across heterogeneous systems.
In order to achieve this goal, the ISO 13606 standard provides a dual-model architecture in which archetypes are extensible schemas of EHR data via their specialization and composition mechanisms.
However, the ISO 13606 standard lacks the formal semantics of archetypes, which makes it difficult to build EHR systems or archetype repositories in a consistent and longitudinal manner.
The goal of the present study was to clarify the archetype semantics of ISO 13606 by means of a formal methodology called **typed lambda calculus**, which has been widely used to define and analyze the semantics of modern programming languages and database systems.
We focus on the variance and immutability of the archetype, because these factors determine the expressive power of archetypes.
We defined a type system that represents the fundamental components of ISO 13606 semantics and analyzed the semantics based on a deductive system of the type theory.
The obtained results indicate that the archetypes should be covariant and immutable schemas in order to guarantee both the structural interoperability of EHR data and the extensibility of archetypes.

## style cheking

~~~
> rake check:all
> rake check:weasel
> rake check:passive
> rake check:style
~~~

