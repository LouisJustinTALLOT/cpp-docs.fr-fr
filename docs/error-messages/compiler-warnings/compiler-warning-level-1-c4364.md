---
title: Avertissement du compilateur (niveau 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: db2774b6a73a989b4e9250719f99122826b486fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643597"
---
# <a name="compiler-warning-level-1-c4364"></a>Avertissement du compilateur (niveau 1) C4364

\#pour l’assembly 'fichier' déjà rencontré à emplacement (numéro_ligne) sans attribut as_friend ; as_friend non appliqué

Un `#using` directive a été répétée pour un fichier de métadonnées donné, mais la `as_friend` qualificateur n’a pas été utilisé dans la première occurrence ; le compilateur ignore le deuxième `as_friend`.

Pour plus d’informations, consultez [assemblys Friend (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant crée un composant.

```
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Exemple

L’exemple suivant génère C4364.

```
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```