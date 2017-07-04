---
title: "Variablen und Argumente | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Variablen und Argumente
In [!INCLUDE[wf](../../../includes/wf-md.md)] stellen Variablen den Speicher von Daten dar, während Argumente den Datenstrom in und aus einer Aktivität bilden.Eine Aktivität verfügt über einen Satz von Argumenten, die die Signatur der Aktivität ausmachen.Darüber hinaus kann eine Aktivität eine Liste von Variablen verwalten. Ein Entwickler kann während des Entwurfs eines Workflows Variablen zu dieser Liste hinzufügen oder daraus löschen.Ein Argument wird mit einem Ausdruck gebunden, der einen Wert zurückgibt.  
  
## Variablen  
 Variablen sind Speicherorte für Daten.Variablen werden als Teil der Definition eines Workflows deklariert.Variablen nehmen zur Laufzeit Werte an, die dann als Teil des Zustands einer Workflowinstanz gespeichert werden.Eine Variablendefinition gibt den Typ der Variable und optional auch ihren Namen an.Im folgenden Code wird gezeigt, wie eine Variable deklariert und ihr mit einer <xref:System.Activities.Statements.Assign%601>\-Aktivität ein Wert zugewiesen wird und wie der Wert mithilfe einer <xref:System.Activities.Statements.WriteLine>\-Aktivität in der Konsole angezeigt wird.  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 Ein Standardwertausdruck kann optional als Teil einer Variablendeklaration angegeben werden.Variablen können auch über Modifizierer verfügen.Wenn z. B. eine Variable schreibgeschützt ist, kann der <xref:System.Activities.VariableModifiers>\-Schreibschutmodifizierer angewendet werden.Im folgenden Beispiel wird eine schreibgeschützte Variable erstellt, die über einen Standardwert verfügt.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## Variablengültigkeit  
 Die Lebensdauer einer Variable zur Laufzeit entspricht der Lebensdauer der Aktivität, von der die Variable deklariert wird.Wenn eine Aktivität abgeschlossen wird, werden ihre Variablen bereinigt, und es kann nicht mehr darauf verwiesen werden.  
  
## Argumente  
 Aktivitätsautoren definieren die Datenflüsse in und aus einer Aktivität mithilfe von Argumenten.Jedes Argument verfügt über eine angegebene Richtung: <xref:System.Activities.ArgumentDirection>, <xref:System.Activities.ArgumentDirection> oder <xref:System.Activities.ArgumentDirection>.  
  
 Die Workflowlaufzeit gewährleistet folgende Aktionen hinsichtlich der zeitlichen Steuerung der Datenverschiebung in und aus Aktivitäten:  
  
1.  Wenn die Ausführung einer Aktivität beginnt, werden die Werte aller Eingabeargumente und Eingabe\-\/Ausgabeargumente berechnet.Beispielsweise entspricht unabhängig davon, wann <xref:System.Activities.Argument.Get%2A> aufgerufen wird, der zurückgegebene Wert dem Wert, der vor dem Aufruf von `Execute` von der Laufzeit berechnet wurde.  
  
2.  Wenn <xref:System.Activities.InOutArgument%601.Set%2A> aufgerufen wird, legt die Laufzeit den Wert sofort fest.  
  
3.  Für Argumente kann optional <xref:System.Activities.Argument.EvaluationOrder%2A> angegeben werden.<xref:System.Activities.Argument.EvaluationOrder%2A> ist ein nullbasierter Wert, der die Reihenfolge angibt, in der das Argument ausgewertet wird.Standardmäßig ist die Auswertungsreihenfolge des Arguments nicht angegeben und und entspricht dem <xref:System.Activities.Argument.UnspecifiedEvaluationOrder>\-Wert.Legen Sie <xref:System.Activities.Argument.EvaluationOrder%2A> auf einen Wert fest, der größer oder gleich null ist, um eine Auswertungsreihenfolge für dieses Argument anzugeben.[!INCLUDE[wf2](../../../includes/wf2-md.md)] wertet Argumente mit einer angegebenen Auswertungsreihenfolge in aufsteigender Reihenfolge aus.Beachten Sie, dass Argumente mit einer nicht angegebenen Auswertungsreihenfolge vor Argumenten mit einer angegebenen Auswertungsreihenfolge ausgewertet werden.  
  
 Ein Aktivitätsautor kann einen stark typisierten Mechanismus zur Bereitstellung seiner Argumente verwenden.Dazu werden Eigenschaften von Typ <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> und <xref:System.Activities.InOutArgument%601> deklariert.Auf diese Weise kann ein Aktivitätsautor einen bestimmten Vertrag für die ein\- und ausgehenden Daten einer Aktivität einrichten.  
  
### Definieren der Argumente einer Aktivität  
 Argumente können für eine Aktivität definiert werden, indem Eigenschaften vom Typ <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> und <xref:System.Activities.InOutArgument%601> angegeben werden.Im folgenden Code wird gezeigt, wie die Argumente für eine `Prompt`\-Aktivität definiert werden, die eine Zeichenfolge akzeptiert und Benutzer anzeigt und eine Zeichenfolge zurückgibt, die die Antwort des Benutzers enthält.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  Aktivitäten, die einen einzelnen Wert zurückgeben, können von <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601> oder <xref:System.Activities.CodeActivity%601> abgeleitet werden.Diese Aktivitäten verfügen über ein klar definiertes <xref:System.Activities.OutArgument%601>\-Objekt mit dem Namen <xref:System.Activities.Activity%601.Result%2A>, das den Rückgabewert der Aktivität enthält.  
  
### Verwenden von Variablen und Argumenten in Workflows  
 Im folgenden Beispiel wird gezeigt, wie Variablen und Argumente in einem Workflow verwendet werden.Der Workflow ist eine Sequenz, die drei Variablen deklariert: `var1`, `var2` und `var3`.Die erste Aktivität im Workflow ist eine `Assign`\-Aktivität, die den Wert der `var2`\-Variable dem Wert der `var1`\-Variable zuweist.Darauf folgt eine `WriteLine`\-Aktivität, die den Wert der `var2`\-Variable druckt.Als Nächstes kommt eine andere `Assign`\-Aktivität, die dem Wert der `var3`\-Variable den Wert der `var2`\-Variable zuweist.Schließlich folgt eine weitere `WriteLine`\-Aktivität, die den Wert der `var3`\-Variable druckt.Die erste `Assign`\-Aktivität verwendet `InArgument<string>` und `OutArgument<string>`\-Objekte, die explizit die Bindungen für die Argumente der Aktivität darstellen.`InArgument<string>` wird für <xref:System.Activities.Statements.Assign.Value%2A> verwendet, weil der Wert durch das <xref:System.Activities.Statements.Assign.Value%2A>\-Argument in die <xref:System.Activities.Statements.Assign%601>\-Aktivität übertragen wird, und `OutArgument<string>` wird für <xref:System.Activities.Statements.Assign.To%2A> verwendet, weil der Wert aus dem <xref:System.Activities.Statements.Assign.To%2A>\-Argument in die Variable übertragen wird.Die zweite `Assign`\-Aktivität erreicht dasselbe Ziel mit einer kompakteren Syntax, die ansonsten äquivalent ist und implizite Umwandlungen verwendet.Die `WriteLine`\-Aktivitäten verwenden ebenfalls die kompakte Syntax.  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =   
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### Verwenden von Variablen und Argumenten in codebasierten Aktivitäten  
 In den vorherigen Beispielen wird gezeigt, wie Argumente und Variablen in Workflows und deklarativen Aktivitäten verwendet werden.Argumente und Variablen werden auch in codebasierten Aktivitäten verwendet.Vom Konzept her ist die Verwendung sehr ähnlich.Variablen stellen Datenspeicher innerhalb der Aktivität dar, und Argumente bezeichnen den Datenstrom in oder aus der Aktivität. Sie werden vom Workflowautor an andere Variablen oder Argumente im Workflow gebunden, die Ursprung und Ziel des Datenstroms darstellen.Um den Wert einer Variable oder eines Arguments in einer Aktivität abzurufen oder festzulegen, muss ein Aktivitätskontext verwendet werden, der die aktuelle Ausführungsumgebung der Aktivität darstellt.Er wird von der Workflowlaufzeit in die <xref:System.Activities.CodeActivity%601.Execute%2A>\-Methode der Aktivität übergeben.In diesem Beispiel wird eine benutzerdefinierte `Add`\-Aktivität definiert, die über zwei <xref:System.Activities.ArgumentDirection>\-Argumente verfügt.Mit der <xref:System.Activities.Argument.Get%2A>\-Methode wird auf den Wert der Argumente zugegriffen. Es wird der Kontext verwendet, der von der Workflowlaufzeit übergeben wurde.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] Arbeiten mit Argumenten, Variablen und Ausdrücken in Code finden Sie unter [Erstellen von Workflows, Aktivitäten und Ausdrücken mit imperativem Code](../../../docs/framework/windows-workflow-foundation//authoring-workflows-activities-and-expressions-using-imperative-code.md) und [Erforderliche Argumente und Überladungsgruppen](../../../docs/framework/windows-workflow-foundation//required-arguments-and-overload-groups.md).