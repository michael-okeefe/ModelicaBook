Interfaces and Implementations
------------------------------

Conceptual Definitions
^^^^^^^^^^^^^^^^^^^^^^

In both of the examples we presented in this chapter, we used
interface definitions as part of the architecture definition process.
The term "interface" doesn't come from Modelica itself, it is a term
common among object-oriented languages.  In Modelica, we can think of
interfaces as models that define all the details of the model **that
are externally visible**.  You can think of an interface as a "shell"
without any internal details.  For this reason, interface models are
almost always marked as ``partial``.

Another important concept is that of an "implementation".  This is
another term borrowed from the world of object-oriented languages.
Whereas an interface is used to simply describe the externally visible
aspects of a model, an implementation includes internal details as
well.  It includes the information required to actually implement that
interface.  In some cases, it may only constitute a partial
implementation (in which case it should also be marked as
``partial``).  In other cases, it may represent the architecture of a
particular subsystem where further implementation details are pushed
one additional level down in the model hierarchy (another case of a
``partial`` model).  But most of the time, these implementations will
be complete (non-``partial``) models for a particular subsystem.

.. _plug-compatibility:

Plug-Compatibility
^^^^^^^^^^^^^^^^^^

The most important thing we need to consider when we talk about
interfaces and implementations is the notion of
**plug-compatibility**.  As we already discussed in our elaboration of
the :ref:`sensor-comparison` example, a model ``X`` is plug-compatible
with a model ``Y`` if for every **public** variable in ``Y``, there is
a corresponding public variable in ``X`` with the same name.
Furthermore, every such variable in ``X`` must itself be
plug-compatible with its counterpart in ``Y``.  This ensures that if
you change a component of type ``Y`` into a component of type ``X``
that everything you need (parameters, connectors, etc) will still be
there and will still be compatible.  **However, please note** that if
``X`` is plug-compatible with ``Y``, this **does not** imply that
``Y`` is plug-compatible with ``X`` (as we will see in a moment).

Generally speaking, most cases where we concern ourselves with
plug-compatibility revolve around whether a given implementation is
plug-compatible with a given interface.  As we've seen in these
examples (and we will review shortly), the configuration management
features in Modelica hinge on the relationship between interfaces and
implementations and the process by which configuration management is
performed is centered around plug-compatibility.

Conclusion
^^^^^^^^^^

The bottom line is that it is very useful to not only think in terms
of interface and implementation models, but also to create models to
formally define interfaces and distinguish them from implementations
since these will be very useful when creating architecture driven
models.
