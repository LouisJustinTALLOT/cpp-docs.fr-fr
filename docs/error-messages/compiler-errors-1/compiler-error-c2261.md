---
title: Erreur du compilateur C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: f23c2a38f8e4d6781af73fb70a25cf4737e2c4e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758773"
---
# <a name="compiler-error-c2261"></a>Erreur du compilateur C2261

'chaîne' : la référence d’assembly n’est pas valide et ne peut pas être résolue

Une valeur n’est pas valide.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> est utilisé pour spécifier un assembly friend. Par exemple, si un fichier. dll souhaite spécifier b. dll comme assembly friend, vous devez spécifier (dans un fichier. dll) : InternalsVisibleTo ("b"). Le runtime permet ensuite à b. dll d’accéder à tous les éléments d’un fichier. dll (à l’exception des types privés).

Pour plus d’informations sur la syntaxe correcte lors de la spécification d’assemblys friend, consultez [Friend AssembliesC++()](../../dotnet/friend-assemblies-cpp.md).

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
