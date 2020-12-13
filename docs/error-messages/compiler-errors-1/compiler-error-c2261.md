---
description: 'En savoir plus sur : erreur du compilateur C2261'
title: Erreur du compilateur C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: c5156a240696f9021613b54cf7013e9372a13b45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134613"
---
# <a name="compiler-error-c2261"></a>Erreur du compilateur C2261

'chaîne' : la référence d’assembly n’est pas valide et ne peut pas être résolue

Une valeur n’est pas valide.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> est utilisé pour spécifier un assembly friend. Par exemple, si a.dll souhaite spécifier b.dll comme assembly friend, vous devez spécifier (dans a.dll) : InternalsVisibleTo ("b"). Le runtime permet ensuite à b.dll d’accéder à tout ce qui se trouve dans a.dll (à l’exception des types privés).

Pour plus d’informations sur la syntaxe correcte lors de la spécification d’assemblys friend, consultez [assemblys friend (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2261.

```cpp
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```
