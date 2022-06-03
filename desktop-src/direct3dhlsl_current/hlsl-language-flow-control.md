# Flow Control

Most hardware is designed to run shader code line by line, executing each HLSL statement once. A flow-control statement determines at run time which block of HLSL statements to execute next. Using a flow-control statement, a shader can loop through a set of statements, or jump (branch) to an instruction other than the one on the next line. Some flow-control statements support static control that is specified at compile time; others offer predicated control which is a per-component decision made at runtime, and still others support dynamic control which is a decision made at run time based on the contents of a variable.

## break Statement

Exit the surrounding loop ([do](dx-graphics-hlsl-do.md), [for](dx-graphics-hlsl-for.md), [while](dx-graphics-hlsl-while.md)).

```HLSL
break;
```

### Parameters

None

## continue Statement

Stop executing the current loop ([do], [for], [while]), update the loop conditions, and begin executing from the top of the loop.

```HLSL
continue;
```

### Parameters

None

## discard Statement

Do not output the result of the current pixel.

```HLSL
discard;
```

### Parameters

None

### Remarks

This statement can only be called from a pixel shader; it is not supported within a geometry shader or a vertex shader.

## do Statement

Execute a series of statements continuously until the conditional expression fails.

```HLSL
[Attribute] do { Statement Block; } while( Conditional );
```

### Parameters

#### `Attribute`

An optional parameter that controls how the statement is compiled.

#### `Statement Block`

One or more `statements`.

#### `Conditional`

A conditional `expression`. The statement block is executed before the expression is evaluated. The loop is exited when the expression evaluates to false.

## for Statement

Iteratively executes a series of statements, based on the evaluation of the conditional expression.

```HLSL
[Attribute] for ( Initializer; Conditional; Iterator ) { Statement Block; }
```

### Parameters

#### `Attribute`

An optional parameter that controls how the statement is compiled.

#### `Initializer`

The initial value of the loop counter.

#### `Conditional`

A conditional `expression`. The statement block is executed before the expression is evaluated. The loop is exited when the expression evaluates to false.

#### `Iterator`

Update the value of the loop counter.

#### `Statement Block`

One or more `statements`.

## if Statement

Conditionally execute a series of statements, based on the evaluation of the conditional expression.

```HLSL
[Attribute] if ( Conditional ) { Statement Block; }
```

### Parameters

#### `Attribute`

An optional parameter that controls how the statement is compiled.

#### `Conditional`

A conditional `expression`. The statement block is executed before the expression is evaluated. The loop is exited when the expression evaluates to false.

#### `Statement Block`

One or more `statements`.

## switch Statement

Transfer control to a different statement block within the switch body depending on the value of a selector.

```HLSL
[Attribute] switch( Selector ) { case 0 : { StatementBlock; } break; case 1 : { StatementBlock; } break; case n : { StatementBlock; } break; default : { StatementBlock; } break;
```

### Parameters

#### `Attribute`

An optional parameter that controls how the statement is compiled.

#### `Selector`

A variable. The case statements inside the curly brackets will each check this variable to see if the SwitchValue matches their particular CaseValue.

#### `Statement Block`

One or more `statements`.

## while Statement

Executes a statement block until the conditional expression fails.

```HLSL
[Attribute] while ( Conditional ) { Statement Block; }
```

### Parameters

#### `Attribute`

An optional parameter that controls how the statement is compiled.

#### `Conditional`

A conditional `expression`. The statement block is executed before the expression is evaluated. The loop is exited when the expression evaluates to false.

#### `Statement Block`

One or more [`statements`](hlsl-language-statements.md).