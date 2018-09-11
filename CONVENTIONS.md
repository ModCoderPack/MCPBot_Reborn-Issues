MCP Naming Conventions
======================

In order to guarantee a consistent style and theme across MCP names, the following conventions
should be adhered to when mapping new things or proposing replacements for existing mappings.
Please refer to this document whenever you do not know how to format or structure a name.

Getting Started
---------------
 - **If you do not know what to name something then *do not name it*. Let someone else do so.**
 - Names should reflect intent, *not* implementation. Check usages rather than just looking at the definition.
 - Names should be concise and memorable. If information can be inferred from context (type, parameters etc.),
   do not include it in the name. This especially applies to fields and methods in a class, where you do not
   need to have the class name in the member's name.
 - Prefer clarification in the documentation comment over verbose names. Conversely, do not give fields,
   methods, or method parameters useless comments.

General
-------
 - All names use US spelling.
 - Acronyms should generally be written all-lowercase, while normal camel case rules still apply.
   For instance, "identifier" becomes `id` as standalone word or at the beginning of a camel case phrase and
   `Id` when used within a phrase.<br>
   There are various exceptions to this rule which apply only when the word does not start with them:
     - axis-aligned bounding boxes: `AxisAlignedBB` → `AABB`
     - named binary tags: `NBT`
     - red, green, blue (and alpha) color components → `RGB(A)`

Type Names
----------
 - New classes, interfaces etc. should follow a suffix-based naming scheme.
   Specifically, this means for any name, `NameType` would be the correct name, where `Type` should be
   derived from the supertypes.
 - Abstract base classes should be prefixed with `Abstract`.
 - Interfaces are prefixed with the letter `I`.
 - Enums should be named directly after the things they are enumerating, in singular form.
   There is no `Enum` prefix/suffix.

**Note:** Long-established names where prefixes are used (subclasses `Block`, `Item` etc.)
do *not* fall under the suffix convention.

### Examples
 - For a new shelf block with an inventory, appropriate names would be `BlockShelf`, `ShelfTileEntity` and
   `ShelfContainer`.

Field Names
-----------
 - `boolean` type fields should *not* start with an *is* prefix unless there is a convincing reason to do so.
 - No prefixes like `the` or suffixes like `Obj`.

Method Names
------------
 - Method names should always start with a verb. Standard conventions for setters and getters apply.
 - Methods returning a `boolean` should have a name beginning with an appropriate prefix from the following list:
     - `can` 
     - `does`
     - `has`
     - `is`
     - `should`
     - `was`
 - 'Event handling' methods should follow an `on<Noun>` theme where the noun is the event's name
   (with redundancies removed).
 - Methods which read or write NBT should be prefixed `read` and `write` respectively.
 - Methods which deseralize or serialize JSON should have a `deserialize` or `serialize` prefix accordingly. 

### Examples
 - The method for handling block right clicks is called `onActivation` (noun form, no redundancy),
   not `onBlockActivated` (past participle, redundant `Block` infix).

Method Parameter Names
----------------------
 - If a name clashes with that of a field or a type name, it should be suffixed with `In`
 - Parameters of certain types should always get named according to the following list:
     - `BlockPos` arguments should be named `pos` when there is a single one, and `*Pos` when there are multiple
     - Parameters of the `IWorldReaderBase` and related type should be `worldIn`