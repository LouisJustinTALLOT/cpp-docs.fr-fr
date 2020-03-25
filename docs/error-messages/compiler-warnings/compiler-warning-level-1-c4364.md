---
title: Avertissement du compilateur (niveau 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 79c8809b4de9d6853aaacec4283bf01d0e89305e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187100"
---
# <a name="compiler-warning-level-1-c4364"></a>Avertissement du compilateur (niveau 1) C4364

\#à l’aide de pour l’assembly’fichier’précédemment vu à l’emplacement (line_number) sans attribut as_friend ; as_friend pas appliqué

Une directive `#using` a été répétée pour un fichier de métadonnées donné, mais le qualificateur `as_friend` n’a pas été utilisé dans la première occurrence ; le compilateur ignore le deuxième `as_friend`.

Pour plus d’informations, consultez [assemblys friendC++()](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant crée un composant.

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4364.

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
