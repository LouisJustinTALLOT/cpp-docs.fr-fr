---
title: Erreur du compilateur C2991
ms.date: 11/04/2016
f1_keywords:
- C2991
helpviewer_keywords:
- C2991
ms.assetid: a87e4404-26e8-4927-b3ee-5d02b3b8bee1
ms.openlocfilehash: bb7d709f757b6da10c8b17d5b30e2c2b86edd85e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366093"
---
# <a name="compiler-error-c2991"></a>Erreur du compilateur C2991

Redéfinition du paramètre de type 'paramètre'

Il existe un conflit de type entre deux définitions génériques ou de modèle de `parameter`. Quand vous définissez plusieurs paramètres génériques ou de modèle, vous devez utiliser des types équivalents.

L’exemple suivant génère l’erreur C2991 :

```
// C2991.cpp
// compile with: /c
template<class T, class T> struct TC {};   // C2991
// try the following line instead
// template<class T, class T2> struct TC {};
```

L’erreur C2991 peut également se produire lors de l’utilisation de génériques :

```
// C2991b.cpp
// compile with: /clr /c
generic<class T,class T> ref struct GC {};   // C2991
// try the following line instead
// generic<class T,class T2> ref struct GC {};
```