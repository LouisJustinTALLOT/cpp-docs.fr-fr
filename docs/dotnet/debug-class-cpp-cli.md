---
title: Classe de débogage (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: eecda10f2fd88b902a54fe9f4dc4de8edc4bc1b0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413560"
---
# <a name="debug-class-ccli"></a>Classe de débogage (C++/CLI)

Lorsque vous utilisez <xref:System.Diagnostics.Debug> dans une application Visual C++, le comportement ne change pas entre un débogage et une version Release.

## <a name="remarks"></a>Notes

Le comportement pour <xref:System.Diagnostics.Trace> est identique au comportement de la classe Debug, mais dépend du symbole TRACE défini. Cela signifie que vous devez `#ifdef` n’importe quel code liées à la Trace pour éviter tout comportement de débogage dans une version Release.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant exécute toujours les instructions de sortie, quelle que soit la compilation s’effectue avec **/DDEBUG** ou **/DTRACE**.

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

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Pour obtenir le comportement attendu (autrement dit, pas de sortie « test » imprimée pour une version Release), vous devez utiliser le `#ifdef` et `#endif` directives. L’exemple de code précédent est modifié ci-dessous pour illustrer ce correctif :

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

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)