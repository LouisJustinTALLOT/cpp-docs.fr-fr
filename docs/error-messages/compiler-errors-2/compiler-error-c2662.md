---
title: Erreur du compilateur C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: b2fa2643898fed510aa7cf0f483b538ebb33b033
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760450"
---
# <a name="compiler-error-c2662"></a>Erreur du compilateur C2662

'fonction' : impossible de convertir le pointeur’This’de’type1 'en’type2 '

Le compilateur n’a pas pu convertir le pointeur `this` de `type1` en `type2`.

Cette erreur peut être causée par l’appel d’une fonction membre non`const` sur un objet `const`.  Solutions possibles :

- Supprimez le `const` de la déclaration de l’objet.

- Ajoutez `const` à la fonction membre.

L’exemple suivant génère l’C2662 :

```cpp
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

Lors de la compilation avec **/CLR**, vous ne pouvez pas appeler une fonction sur un `const` ou `volatile` type managé qualifié. Vous ne pouvez pas déclarer une fonction membre const d’une classe managée, donc vous ne pouvez pas appeler des méthodes sur des objets managés const.

```cpp
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

L’exemple suivant génère l’C2662 :

```cpp
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```
