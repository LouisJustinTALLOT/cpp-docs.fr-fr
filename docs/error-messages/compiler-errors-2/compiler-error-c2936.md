---
title: Erreur du compilateur C2936
ms.date: 11/04/2016
f1_keywords:
- C2936
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
ms.openlocfilehash: 547690302661656cc5368f5969432de68ac91e3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302954"
---
# <a name="compiler-error-c2936"></a>Erreur du compilateur C2936

'class' : type-class-id redéfini comme variable globale de données

Vous ne pouvez pas utiliser une classe générique ni de modèle comme variable globale de données.

Cette erreur peut être provoquée par une mise en correspondance incorrecte des accolades.

L’exemple suivant génère l’erreur C2936 :

```
// C2936.cpp
// compile with: /c
template<class T> struct TC { };
int TC<int>;   // C2936

// OK
struct TC2 { };
int TC2;
```

L’erreur C2936 peut également se produire lors de l’utilisation de génériques :

```
// C2936b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
int GC<int>;   // C2936

// OK
ref struct GC2 {};
int GC2;
```