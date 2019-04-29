---
title: Erreur du compilateur C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: 2df788efd93fb531822d858ea5aee1722487db81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387035"
---
# <a name="compiler-error-c2261"></a>Erreur du compilateur C2261

'string' : référence d’assembly n’est pas valide et ne peut pas être résolue

Une valeur n’était pas valide.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> permet de spécifier un assembly friend. Par exemple, si a.dll souhaite spécifier b.dll comme assembly friend, vous devez spécifier (dans a.dll) : InternalsVisibleTo("b"). Le runtime permet ensuite à b.dll accéder à tous les éléments de a.dll (à l’exception des types privés).

Pour plus d’informations sur la syntaxe correcte lors de la spécification des assemblys friend, consultez [assemblys Friend (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C2261.

```
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```