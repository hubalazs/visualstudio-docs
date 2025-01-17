---
title: .NET formatting conventions for EditorConfig
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
  - "CSharp"
  - "VB"
helpviewer_keywords:
  - "formatting conventions [EditorConfig]"
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "dotnet"
  - "dotnetcore"
---
# Formatting conventions

Formatting conventions for EditorConfig for Visual Studio fall into these categories:

- [.NET formatting settings](#net-formatting-settings)

- [C# formatting settings](#c-formatting-settings)

## Rule format

Rules for formatting conventions have the following format:

`rule_name = value`

For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`. For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule. You don't specify a severity.

## .NET formatting settings

The formatting rules in this section apply to C# and Visual Basic code.

- [Organize usings](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### Organize using directives

These formatting rules concern the sorting and display of `using` directives and `Imports` statements.

Example *.editorconfig* file:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### dotnet\_sort\_system\_directives_first

|||
|-|-|
| **Rule name** | dotnet_sort_system_directives_first |
| **Applicable languages** | C# and Visual Basic |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Sort System.* `using` directives alphabetically, and place them before other using directives.<br /><br />`false` - Do not place System.* `using` directives before other `using` directives. |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### dotnet\_separate\_import\_directive\_groups

|||
|-|-|
| **Rule name** | dotnet_separate_import_directive_groups |
| **Applicable languages** | C# and Visual Basic |
| **Introduced version** | Visual Studio 2017 version 15.5 |
| **Values** | `true` - Place a blank line between `using` directive groups.<br /><br />`false` - Do not place a blank line between `using` directive groups. |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## C# formatting settings

The formatting rules in this section apply only to C# code.

- [Newline options](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Indentation options](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Spacing options](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Wrap options](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks

### New-line options

These formatting rules concern the use of new lines to format code.

Example *.editorconfig* file:

```ini
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### csharp\_new\_line\_before\_open_brace

This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line. For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied. To specify multiple code elements, separate them with a comma (,).

|||
|-|-|
| **Rule name** | csharp_new_line_before_open_brace |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `all` - Require braces to be on a new line for all expressions ("Allman" style).<br /><br />`none` - Require braces to be on the same line for all expressions ("K&R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style). |
| **Visual Studio default** | `all` |

Code examples:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### csharp\_new\_line\_before_else

|||
|-|-|
| **Rule name** | csharp_new_line_before_else |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Place `else` statements on a new line.<br /><br />`false` - Place `else` statements on the same line. |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### csharp\_new\_line\_before_catch

|||
|-|-|
| **Rule name** | csharp_new_line_before_catch |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Place `catch` statements on a new line.<br /><br />`false` - Place `catch` statements on the same line. |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### csharp\_new\_line\_before_finally

|||
|-|-|
| **Rule name** | csharp_new_line_before_finally |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Require `finally` statements to be on a new line after the closing brace.<br /><br />`false` - Require `finally` statements to be on the same line as the closing brace. |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### csharp\_new\_line\_before\_members\_in\_object_initializers

|||
|-|-|
| **Rule name** | csharp_new_line_before_members_in_object_initializers |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Require members of object initializers to be on separate lines<br /><br />`false` - Require members of object initializers to be on the same line |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### csharp\_new\_line\_before\_members\_in\_anonymous_types

|||
|-|-|
| **Rule name** | csharp_new_line_before_members_in_anonymous_types |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Require members of anonymous types to be on separate lines<br /><br />`false` - Require members of anonymous types to be on the same line |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Rule name** | csharp_new_line_between_query_expression_clauses |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Require elements of query expression clauses to be on separate lines<br /><br />`false` - Require elements of query expression clauses to be on the same line |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### Indentation options

These formatting rules concern the use of indentation to format code.

Example *.editorconfig* file:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### csharp\_indent\_case_contents

|||
|-|-|
| **Rule name** | csharp_indent_case_contents |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Indent `switch` case contents<br /><br />`false` - Do not indent `switch` case contents |
| **Visual Studio default** | `true` |

- When this rule is set to **true**, i.
- When this rule is set to **false**, d.

Code examples:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### csharp\_indent\_switch_labels

|||
|-|-|
| **Rule name** | csharp_indent_switch_labels |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Indent `switch` labels<br /><br />`false` - Do not indent `switch` labels |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### csharp\_indent_labels

|||
|-|-|
| **Rule name** | csharp_indent_labels |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `flush_left` - Labels are placed at the leftmost column<br /><br />`one_less_than_current` - Labels are placed at one less indent to the current context<br /><br />`no_change` - Labels are placed at the same indent as the current context |
| **Visual Studio default** | `no_change` |

Code examples:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### csharp_indent_block_contents

|||
|-|-|
| **Rule name** | csharp_indent_block_contents |
| **Applicable languages** | C# |
| **Values** | `true` - <br /><br />`false` -  |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### csharp_indent_braces

|||
|-|-|
| **Rule name** | csharp_indent_braces |
| **Applicable languages** | C# |
| **Values** | `true` - <br /><br />`false` -  |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### csharp_indent_case_contents_when_block

|||
|-|-|
| **Rule name** | csharp_indent_case_contents_when_block |
| **Applicable languages** | C# |
| **Values** | `true` - <br /><br />`false` -  |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### Spacing options

These formatting rules concern the use of space characters to format code.

Example *.editorconfig* file:

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### csharp\_space\_after_cast

|||
|-|-|
| **Rule name** | csharp_space_after_cast |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Place a space character between a cast and the value<br /><br />`false` - Remove space between the cast and the value |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Rule name** | csharp_space_after_keywords_in_control_flow_statements |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Place a space character after a keyword in a control flow statement such as a `for` loop<br /><br />`false` - Remove space after a keyword in a control flow statement such as a `for` loop |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### csharp_space_between_parentheses

|||
|-|-|
| **Rule name** | csharp_space_between_parentheses |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `control_flow_statements` - Place space between parentheses of control flow statements<br /><br />`expressions` - Place space between parentheses of expressions<br /><br />`type_casts` - Place space between parentheses in type casts |
| **Visual Studio default** | `false` |

If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.

Code examples:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **Rule name** | csharp_space_before_colon_in_inheritance_clause |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.7 |
| **Values** | `true` - Place a space character before the colon for bases or interfaces in a type declaration<br /><br />`false` - Remove space before the colon for bases or interfaces in a type declaration |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **Rule name** | csharp_space_after_colon_in_inheritance_clause |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.7 |
| **Values** | `true` - Place a space character after the colon for bases or interfaces in a type declaration<br /><br />`false` - Remove space after the colon for bases or interfaces in a type declaration |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### csharp\_space\_around\_binary_operators

|||
|-|-|
| **Rule name** | csharp_space_around_binary_operators |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.7 |
| **Values** | `before_and_after` - Insert space before and after the binary operator<br /><br />`none` - Remove spaces before and after the binary operator<br /><br />`ignore` - Ignore spaces around binary operators |
| **Visual Studio default** | `before_and_after` |

If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.

Code examples:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Rule name** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list<br /><br />`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Rule name** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.7 |
| **Values** | `true` - Insert space within empty parameter list parentheses for a method declaration<br /><br />`false` - Remove space within empty parameter list parentheses for a method declaration |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### csharp_space_between_method_declaration_name_and_open_parenthesis

|||
|-|-|
| **Rule name** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Applicable languages** | C# |
| **Values** | `true` - Place a space character between the method name and opening parenthesis in the method declaration<br /><br />`false` - Remove space characters between the method name and opening parenthesis in the method declaration |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Rule name** | csharp_space_between_method_call_parameter_list_parentheses |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call<br /><br />`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Rule name** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.7 |
| **Values** | `true` - Insert space within empty argument list parentheses<br /><br />`false` - Remove space within empty argument list parentheses |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Rule name** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.7 |
| **Values** | `true` - Insert space between method call name and opening parenthesis<br /><br />`false` - Remove space between method call name and opening parenthesis |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### csharp_space_after_comma

|||
|-|-|
| **Rule name** | csharp_space_after_comma |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space after a comma<br /><br />`false` - Remove space after a comma |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### csharp_space_before_comma

|||
|-|-|
| **Rule name** | csharp_space_before_comma |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space before a comma<br /><br />`false` - Remove space before a comma |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### csharp_space_after_dot

|||
|-|-|
| **Rule name** | csharp_space_after_dot |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space after a dot<br /><br />`false` - Remove space after a dot |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### csharp_space_before_dot

|||
|-|-|
| **Rule name** | csharp_space_before_dot |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space before a dot <br /><br />`false` - Remove space before a dot |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### csharp_space_after_semicolon_in_for_statement

|||
|-|-|
| **Rule name** | csharp_space_after_semicolon_in_for_statement |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space after each semicolon in a `for` statement<br /><br />`false` - Remove space after each semicolon in a `for` statement |
| **Visual Studio default** | `true` |

Code examples:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### csharp_space_before_semicolon_in_for_statement

|||
|-|-|
| **Rule name** | csharp_space_before_semicolon_in_for_statement |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space before each semicolon in a `for` statement <br /><br />`false` - Remove space before each semicolon in a `for` statement |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### csharp_space_around_declaration_statements

|||
|-|-|
| **Rule name** | csharp_space_around_declaration_statements |
| **Applicable languages** | C# |
| **Values** | `ignore` - Don't remove extra space characters in declaration statements<br /><br />`false` - Remove extra space characters in declaration statements |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### csharp_space_before_open_square_brackets

|||
|-|-|
| **Rule name** | csharp_space_before_open_square_brackets |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space before opening square brackets `[` <br /><br />`false` - Remove space before opening square brackets `[` |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### csharp_space_between_empty_square_brackets

|||
|-|-|
| **Rule name** | csharp_space_between_empty_square_brackets |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space between empty square brackets `[ ]` <br /><br />`false` - Remove space between empty square brackets `[]` |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### csharp_space_between_square_brackets

|||
|-|-|
| **Rule name** | csharp_space_between_square_brackets |
| **Applicable languages** | C# |
| **Values** | `true` - Insert space characters in non-empty square brackets `[ 0 ]` <br /><br />`false` - Remove space characters in non-empty square brackets `[0]` |
| **Visual Studio default** | `false` |

Code examples:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### Wrap options

These formatting rules concern the use of single lines versus separate lines for statements and code blocks.

Example *.editorconfig* file:

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### csharp_preserve_single_line_statements

|||
|-|-|
| **Rule name** | csharp_preserve_single_line_statements |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Leave statements and member declarations on the same line<br /><br />`false` - Leave statements and member declarations on different lines |
| **Visual Studio default** | `true` |

Code examples:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### csharp_preserve_single_line_blocks

|||
|-|-|
| **Rule name** | csharp_preserve_single_line_blocks |
| **Applicable languages** | C# |
| **Introduced version** | Visual Studio 2017 version 15.3 |
| **Values** | `true` - Leave code block on single line<br /><br />`false` - Leave code block on separate lines |
| **Visual Studio default** | `true` |

Code examples:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

## See also

- [Language conventions](editorconfig-language-conventions.md)
- [Naming conventions](editorconfig-naming-conventions.md)
- [.NET coding convention settings for EditorConfig](editorconfig-code-style-settings-reference.md)
