---
title: Erreur du compilateur C2937
ms.date: 11/04/2016
f1_keywords:
- C2937
helpviewer_keywords:
- C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
ms.openlocfilehash: 8ad25dbcec4ee8a8ed49449cf9e64ebae4af1321
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541009"
---
# <a name="compiler-error-c2937"></a>Erreur du compilateur C2937

'class' : type-class-id redéfini comme typedef global

Vous ne pouvez pas utiliser une classe générique ou de modèle comme `typedef`global.

L’exemple suivant génère l’erreur C2937 :

```
// C2937.cpp
// compile with: /c
template<class T>
struct TC { };
typedef int TC<int>;   // C2937
typedef TC<int> c;   // OK
```

L’erreur C2937 peut également se produire lors de l’utilisation de génériques :

```
// C2937b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };
typedef int GC<int>;   // C2937
typedef GC<int> xx;   // OK
```