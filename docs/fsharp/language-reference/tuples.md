---
title: Tupel (F#)
description: "Informationen Sie zu F#-Tupel, eine Gruppierung von unbenannte jedoch geordnete Werte möglicherweise von anderen Typen."
keywords: Visual F#, F#, funktionale Programmierung
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35069073-9a82-410f-8dea-912e2a152e6d
ms.openlocfilehash: c6a0565ac7022928f5c2bdad5387d896c6c3d387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="tuples"></a><span data-ttu-id="ebfa6-104">Tupel</span><span class="sxs-lookup"><span data-stu-id="ebfa6-104">Tuples</span></span>

<span data-ttu-id="ebfa6-105">Ein *Tupel* ist eine Gruppierung von unbenannte jedoch geordnete Werte möglicherweise von anderen Typen.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-105">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="ebfa6-106">Tupel kann entweder Verweistypen oder Strukturen sein.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-106">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebfa6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ebfa6-107">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a><span data-ttu-id="ebfa6-108">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ebfa6-108">Remarks</span></span>
<span data-ttu-id="ebfa6-109">Jede *Element* in der vorherigen Syntax kann jeder gültiger F#-Ausdruck sein.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-109">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="ebfa6-110">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ebfa6-110">Examples</span></span>
<span data-ttu-id="ebfa6-111">Beispiele für Tupel sind Paare, Tripel, usw., der gleichen oder unterschiedliche Typen.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-111">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="ebfa6-112">Einige Beispiele sind in den folgenden Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-112">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a><span data-ttu-id="ebfa6-113">Abrufen einzelner Werte</span><span class="sxs-lookup"><span data-stu-id="ebfa6-113">Obtaining Individual Values</span></span>
<span data-ttu-id="ebfa6-114">Sie können mithilfe des Mustervergleichs zugreifen, und weisen Sie Aliasnamen für Tupelelemente, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-114">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="ebfa6-115">Sie können auch ein Tupel über Mustervergleich außerhalb von Löschen einer `match` Ausdruck über `let` Bindung:</span><span class="sxs-lookup"><span data-stu-id="ebfa6-115">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="ebfa6-116">Oder Sie können Muster, die als Eingaben für Funktionen auf Tupel übereinstimmen:</span><span class="sxs-lookup"><span data-stu-id="ebfa6-116">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="ebfa6-117">Wenn Sie nur ein Element des Tupels benötigen, kann das Platzhalterzeichen (Unterstrich) verwendet werden, um zu vermeiden, erstellen einen neuen Namen für einen Wert an, dem Sie nicht benötigen.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-117">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="ebfa6-118">Kopieren Elemente aus einem Verweis Tupel in einer Struktur Tupel ist einfach:</span><span class="sxs-lookup"><span data-stu-id="ebfa6-118">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="ebfa6-119">Die Funktionen `fst` und `snd` (nur Tupel verweisen) die ersten und zweiten Sie Elemente eines Tupels bzw..</span><span class="sxs-lookup"><span data-stu-id="ebfa6-119">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="ebfa6-120">Keine integrierte Funktion, die das dritte Element der Tripel zurückgibt vorhanden ist, aber Sie können problemlos wie folgt schreiben.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-120">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="ebfa6-121">Im Allgemeinen ist es besser, die mithilfe des Mustervergleichs Zugriff auf Tupelelemente der einzelnen.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-121">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="ebfa6-122">Verwenden von Tupeln</span><span class="sxs-lookup"><span data-stu-id="ebfa6-122">Using Tuples</span></span>
<span data-ttu-id="ebfa6-123">Tupel bieten eine einfache Möglichkeit, mehrere Werte aus einer Funktion zurückgeben, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-123">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="ebfa6-124">In diesem Beispiel führt die Ganzzahldivision und gibt das gerundete Ergebnis des Vorgangs als erste Member eines Paars Tupel und den Rest als zweite Element des Paars.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-124">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="ebfa6-125">Tupel können auch als Funktionsargumente verwendet werden, wenn sollten vermieden werden die implizitem currying von Funktionsargumenten, die durch die üblichen Funktionssyntax impliziert ist.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-125">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="ebfa6-126">Der üblichen Syntax zum Definieren der Funktion `let sum a b = a + b` ermöglicht es Ihnen, eine Funktion, ist der partiellen Anwendung von das erste Argument der Funktion, zu definieren, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-126">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="ebfa6-127">Verwenden Sie ein Tupel als Parameter wird currying deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-127">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="ebfa6-128">Weitere Informationen finden Sie unter "Partielle Anwendung von Argumenten" im [Funktionen](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebfa6-128">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="ebfa6-129">Namen von Tupeltypen</span><span class="sxs-lookup"><span data-stu-id="ebfa6-129">Names of Tuple Types</span></span>
<span data-ttu-id="ebfa6-130">Wenn Sie den Namen eines Typs, die ein Tupel ist schreiben, verwenden Sie die `*` Symbol, um Elemente zu trennen.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-130">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="ebfa6-131">Für ein Tupel, aus denen besteht eine `int`, `float`, und ein `string`, wie z. B. `(10, 10.0, "ten")`, Typs würde wie folgt geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-131">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="ebfa6-132">Interoperation mit c# Tupel</span><span class="sxs-lookup"><span data-stu-id="ebfa6-132">Interoperation with C# Tuples</span></span>

<span data-ttu-id="ebfa6-133">C#-7 eingeführt Tupel in der Sprache an.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-133">C# 7 introduced tuples to the language.</span></span>  <span data-ttu-id="ebfa6-134">Tupel in c# und sind Strukturen und Struktur Tupel in f# gleich sind.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-134">Tuples in C# and are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="ebfa6-135">Wenn Sie mit zusammenarbeiten müssen müssen c# Tupel verwendet, Sie Struktur Tupel.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-135">If you need to interoperate with C# uses tuples, you must use struct tuples.</span></span>

<span data-ttu-id="ebfa6-136">Dies ist einfach.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-136">This is easy to do.</span></span>  <span data-ttu-id="ebfa6-137">Angenommen Sie, Sie verfügen über ein Tupel an eine C#-Klasse übergeben und dann verwenden das Ergebnis, das auch ein Tupel ist:</span><span class="sxs-lookup"><span data-stu-id="ebfa6-137">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="ebfa6-138">Sie können in Ihrem f#-Code dann ein Tupel Struktur als Parameter übergeben und nutzen das Ergebnis als Struktur Tupel.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-138">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="ebfa6-139">Konvertieren zwischen Verweis Tupel und Tupel-Struktur</span><span class="sxs-lookup"><span data-stu-id="ebfa6-139">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="ebfa6-140">Da Verweis Tupel und Struct-Tuples eine ganz andere zugrunde liegenden Darstellung haben, sind sie nicht implizit konvertiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-140">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="ebfa6-141">D. h. kompiliert nicht dem folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="ebfa6-141">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="ebfa6-142">Sie müssen das Muster auf ein Tupel übereinstimmen und die andere die Bestandteile zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-142">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="ebfa6-143">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ebfa6-143">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="ebfa6-144">Kompilierte Form der Verweis Tupel</span><span class="sxs-lookup"><span data-stu-id="ebfa6-144">Compiled Form of Reference Tuples</span></span>
<span data-ttu-id="ebfa6-145">Dieser Abschnitt erklärt die Form der Tupel bei der Prozedur-sind.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-145">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="ebfa6-146">Die Informationen hier nicht lesen, es sei denn, Sie .NET Framework 3.5 abzielen notwendig oder niedriger.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-146">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="ebfa6-147">Tupel werden in Objekte eines von mehreren generischen Typen, die alle benannten kompiliert `System.Tuple`, für die Stelligkeit oder die Anzahl von Typparametern überladen sind.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-147">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="ebfa6-148">Tuple-Typen werden in dieser Form angezeigt, bei der Anzeige in einer anderen Sprache, z. B. c# oder Visual Basic, oder wenn Sie ein Tool verwenden, die f#-Konstrukte nicht beachtet.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-148">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="ebfa6-149">Die `Tuple` Typen in .NET Framework 4 eingeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-149">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="ebfa6-150">Wenn Sie eine frühere Version von .NET Framework abzielen, verwendet der Compiler-Versionen [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) aus der Version 2.0 der f#-Kernbibliothek.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-150">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="ebfa6-151">Die Typen in dieser Bibliothek dienen nur für Anwendungen, die auf dem 2.0, 3.0 und 3.5 Versionen von .NET Framework abzielen.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-151">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="ebfa6-152">Typweiterleitung wird verwendet, um sicherzustellen, dass binäre Kompatibilität zwischen .NET Framework 2.0 und .NET Framework 4 F#-Komponenten.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-152">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="ebfa6-153">Kompilierte Form der Tupel-Struktur</span><span class="sxs-lookup"><span data-stu-id="ebfa6-153">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="ebfa6-154">Struct-Tupel (z. B. `struct (x, y)`), unterscheiden sich grundlegend von Verweis Tupel.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-154">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="ebfa6-155">Sie werden in kompiliert die <xref:System.ValueTuple> Typ, durch Stelligkeit oder die Anzahl von Typparametern überlastet.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-155">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="ebfa6-156">Gleichwertig zu [C#-7-Tupel](../../csharp/tuples.md) und [Visual Basic 2017 Tupel](../../visual-basic/programming-guide/language-features/data-types/tuples.md), und bietet Interoperabilität bidirektional.</span><span class="sxs-lookup"><span data-stu-id="ebfa6-156">They are equivalent to [C# 7 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebfa6-157">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ebfa6-157">See Also</span></span>
[<span data-ttu-id="ebfa6-158">F#-Sprachreferenz</span><span class="sxs-lookup"><span data-stu-id="ebfa6-158">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="ebfa6-159">F#-Typen</span><span class="sxs-lookup"><span data-stu-id="ebfa6-159">F# Types</span></span>](fsharp-types.md)