---
title: Avertissement du compilateur (niveau 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 7f1c71cb3cd6a99d4ed9960032813e7cebca7591
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685077"
---
# <a name="compiler-warning-level-1-c4364"></a>Avertissement du compilateur (niveau 1) C4364

\#utilisation de pour l’assembly’fichier’précédemment rencontré à l’emplacement (line_number) sans attribut as_friend ; as_friend pas appliqué

Une `#using` directive a été répétée pour un fichier de métadonnées donné, mais le **`as_friend`** qualificateur n’a pas été utilisé dans la première occurrence ; le compilateur ignorera la seconde **`as_friend`** .

Pour plus d’informations, consultez [assemblys friend (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="examples"></a>Exemples

L’exemple suivant crée un composant.

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

L’exemple suivant génère l’C4364.

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
