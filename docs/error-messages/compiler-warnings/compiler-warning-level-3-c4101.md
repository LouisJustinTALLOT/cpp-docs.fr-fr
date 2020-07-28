---
title: Avertissement du compilateur (niveau 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: f9d3875fdc17def1e7d3bcb72149c5faf90f656a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220052"
---
# <a name="compiler-warning-level-3-c4101"></a>Avertissement du compilateur (niveau 3) C4101

'identificateur' : variable locale non référencée

La variable locale n’est jamais utilisée. Cet avertissement se produit dans la situation évidente :

```cpp
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

Toutefois, cet avertissement se produit également lors de l’appel d’une **`static`** fonction membre par le biais d’une instance de la classe :

```cpp
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

Dans ce cas, le compilateur utilise des informations sur `si` pour accéder à la **`static`** fonction, mais l’instance de la classe n’est pas nécessaire pour appeler la **`static`** fonction ; par conséquent, l’avertissement. Pour résoudre cet avertissement, vous pouvez :

- Ajoutez un constructeur, dans lequel le compilateur utiliserait l’instance de `si` dans l’appel à `func` .

- Supprimez le **`static`** mot clé de la définition de `func` .

- Appelez la **`static`** fonction explicitement : `int y = S::func();` .
