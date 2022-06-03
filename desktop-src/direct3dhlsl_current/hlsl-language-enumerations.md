# Enumerations

An enumeration is a user-defined type that consists of a set of named integral constants.

```syntax
enum [identifier] [: type] {enum-list};

enum [class] [identifier] [: type] {enum-list};
```

>**note** Follows C++ 11 enumeration rules.

## Parameters

### `identifier`

The type name given to the enumeration.

### `type`

The underlying type of the enumerators. The type may be any [`integer`](hlsl-variables-dataTypes.md#int) or [`unsigned integer`](hlsl-variables-dataTypes.md#uint) type.

### `enum-list`

Comma-separated list of the enumerators in the enumeration. Every enumerator or variable name in the scope must be unique. However, the values can be duplicated.  In a unscoped enum, the scope is the surrounding scope; in a scoped enum, the scope is the <i>enum-list</i> itself. In a scoped enum, the list may be empty which in effect defines a new [`integer`](hlsl-variables-dataTypes.md#int) or [`unsigned integer`](hlsl-variables-dataTypes.md#uint) type.

### `class`

By using this keyword in the declaration, you specify the enum is scoped, and an <i>identifier</i> must be provided.

## Examples

### enum

The following examples demonstrate possible usages with outcomes of `enum`.

```hlsl
// default declaration
// Diamonds = 0, Hearts = 1, Clubs = 2, Spades = 3
enum Suit { Diamonds, Hearts, Clubs, Spades };

// integer specification declaration
// Diamonds = 0, Hearts = 1, Clubs = 2, Spades = 3
enum Suit : int { Diamonds, Hearts, Clubs, Spades };

// when using enum without enum class
// can access values without the containing identifier
Suit mySuit = Diamonds;

// can also use the scope resolution operator to access enum values
Suit mySuit = Suit::Diamonds;
```

### enum class
// default enum class declaration
// Suit::Diamonds = 0, Suit::Hearts = 1, Suit::Clubs = 2, Suit::Spades = 3
enum class Suit { Diamonds, Hearts, Clubs, Spades };

// integer specification declaration
// Suit::Diamonds = 0, Suit::Hearts = 1, Suit::Clubs = 2, Suit::Spades = 3
enum class Suit : int { Diamonds, Hearts, Clubs, Spades };

// first value initialized
// Suit::Diamonds = 1, Suit::Hearts = 2, Suit::Clubs = 3, Suit::Spades = 4
enum class Suit { Diamonds = 1, Hearts, Clubs, Spades };

// multiple values initialized
// Suit::Diamonds = 5, Suit::Hearts = 6, Suit::Clubs = 9, Suit::Spades = 10
enum class Suit { Diamonds = 5, Hearts, Clubs = 9, Spades };

// overlap values initialized
// Suit::Diamonds = 5, Suit::Hearts = 6, Suit::Clubs = 5, Suit::Spades = 6
enum class Suit { Diamonds = 5, Hearts, Clubs = 5, Spades };

// to access, use scope resolution operator
Suit mySuit = Suit::Diamonds;
```