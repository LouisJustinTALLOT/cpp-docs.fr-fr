---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: ccf544608bcba83af17702767562ef93d775b5a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227255"
---
# <a name="novtable"></a>novtable

**Spécifique à Microsoft**

Il s’agit d’un **`__declspec`** attribut étendu.

Cette forme de **`__declspec`** peut être appliquée à toute déclaration de classe, mais ne doit être appliquée qu’aux classes d’interface pures, c’est-à-dire aux classes qui ne seront jamais instanciées par elles-mêmes. **`__declspec`** Empêche le compilateur de générer du code pour initialiser le vfptr dans le (s) constructeur (s) et le destructeur de la classe. Dans de nombreux cas, cela supprime les seules références à la vtable qui sont associés à la classe et, par conséquent, l'éditeur de liens supprimera cette vtable. L’utilisation de cette forme de **`__declspec`** peut entraîner une réduction significative de la taille du code.

Si vous tentez d’instancier une classe marquée avec, **`novtable`** puis d’accéder à un membre de classe, vous recevrez une violation d’accès (AV).

## <a name="example"></a>Exemple

```cpp
// novtable.cpp
#include <stdio.h>

struct __declspec(novtable) X {
   virtual void mf();
};

struct Y : public X {
   void mf() {
      printf_s("In Y\n");
   }
};

int main() {
   // X *pX = new X();
   // pX->mf();   // Causes a runtime access violation.

   Y *pY = new Y();
   pY->mf();
}
```

```Output
In Y
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[`__declspec`](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
