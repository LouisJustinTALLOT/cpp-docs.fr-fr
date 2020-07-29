---
title: Avertissement du compilateur (niveau 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 5423a5525f9bef4d949bfee2de058fe19d0ec181
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220039"
---
# <a name="compiler-warning-level-1-c4364"></a>Avertissement du compilateur (niveau 1) C4364

\#utilisation de pour l’assembly’fichier’précédemment rencontré à l’emplacement (line_number) sans attribut as_friend ; as_friend pas appliqué

Une `#using` directive a été répétée pour un fichier de métadonnées donné, mais le **`as_friend`** qualificateur n’a pas été utilisé dans la première occurrence ; le compilateur ignorera la seconde **`as_friend`** .

Pour plus d’informations, consultez [assemblys friend (C++)](../../dotnet/friend-assemblies-cpp.md).

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
