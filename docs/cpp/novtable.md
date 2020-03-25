---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: d101e73f2f8d476c50b1b80b8daa7994151d43af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177831"
---
# <a name="novtable"></a>novtable

**Section spécifique de Microsoft**

Il s’agit d’un **__declspec** attribut étendu.

Cette forme de **__declspec** peut être appliquée à toute déclaration de classe, mais ne doit être appliquée qu’aux classes d’interface pures, c’est-à-dire aux classes qui ne seront jamais instanciées par elles-mêmes. Le **__declspec** empêche le compilateur de générer du code pour initialiser le vfptr dans le (s) constructeur (s) et le destructeur de la classe. Dans de nombreux cas, cela supprime les seules références à la vtable qui sont associés à la classe et, par conséquent, l'éditeur de liens supprimera cette vtable. L’utilisation de cette forme de **__declspec** peut entraîner une réduction significative de la taille du code.

Si vous tentez d’instancier une classe marquée avec **novtable** , puis d’accéder à un membre de classe, vous recevrez une violation d’accès (AV).

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

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
