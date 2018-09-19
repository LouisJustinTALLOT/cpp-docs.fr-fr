---
title: Erreur du compilateur C2936 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2936
dev_langs:
- C++
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 839d2f3dd005e4bd8bd697c74e5940a0331c1acc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054244"
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