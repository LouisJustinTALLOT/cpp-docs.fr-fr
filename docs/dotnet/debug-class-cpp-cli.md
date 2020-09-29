---
title: Classe de débogage (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 47e1b949cb6e998508a3bd362b1c74961cf4cc23
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414150"
---
# <a name="debug-class-ccli"></a>Classe de débogage (C++/CLI)

Lors de l’utilisation <xref:System.Diagnostics.Debug> de dans une application Visual C++, le comportement ne change pas entre une version Debug et une version Release.

## <a name="remarks"></a>Notes

Le comportement de <xref:System.Diagnostics.Trace> est identique à celui de la classe Debug, mais dépend de la trace Symbol définie. Cela signifie que vous devez disposer `#ifdef` d’un code lié à la trace pour empêcher le comportement de débogage dans une version Release.

## <a name="example-always-executes-output-statements"></a>Exemple : exécute toujours les instructions OUTPUT

### <a name="description"></a>Description

L’exemple suivant exécute toujours les instructions de sortie, que vous compiliiez avec **/DDEBUG** ou **/DTrace**.

### <a name="code"></a>Code

```cpp
// mcpp_debug_class.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
   Trace::Unindent();

   Debug::WriteLine("test");
}
```

### <a name="output"></a>Sortie

```Output
    Entering Main
Hello World.
    Exiting Main
test
```

## <a name="example-use-ifdef-and-endif-directives"></a>Exemple : utiliser des directives #ifdef et #endif

### <a name="description"></a>Description

Pour obtenir le comportement attendu (autrement dit, aucune sortie « test » imprimée pour une version Release), vous devez utiliser les `#ifdef` `#endif` directives et. L’exemple de code précédent est modifié ci-dessous pour illustrer ce correctif :

### <a name="code"></a>Code

```cpp
// mcpp_debug_class2.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();

#ifdef TRACE   // checks for a debug build
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
#endif
   Trace::Unindent();

#ifdef DEBUG   // checks for a debug build
   Debug::WriteLine("test");
#endif   //ends the conditional block
}
```

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
