---
title: Avertissement du compilateur (niveau 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: 0ac34fbaf4cbb54583394dff5b8645fe56b8b9cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199043"
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

Toutefois, cet avertissement se produit également lors de l’appel d’une fonction membre **statique** via une instance de la classe :

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

Dans ce cas, le compilateur utilise des informations sur `si` pour accéder à la fonction **statique** , mais l’instance de la classe n’est pas nécessaire pour appeler la fonction **statique** . par conséquent, l’avertissement. Pour résoudre cet avertissement, vous pouvez :

- Ajoutez un constructeur, dans lequel le compilateur utiliserait l’instance de `si` dans l’appel à `func`.

- Supprimez le mot clé **static** de la définition de `func`.

- Appelez la fonction **statique** explicitement : `int y = S::func();`.
