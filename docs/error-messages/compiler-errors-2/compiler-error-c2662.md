---
description: 'En savoir plus sur : erreur du compilateur C2662'
title: Erreur du compilateur C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: 98a82773c5befe8a125031ab3aac355f582aa15a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170007"
---
# <a name="compiler-error-c2662"></a>Erreur du compilateur C2662

'fonction' : impossible de convertir le pointeur’This’de’type1 'en’type2 '

Le compilateur n’a pas pu convertir le **`this`** pointeur de `type1` en `type2` .

Cette erreur peut être causée par l’appel d’une **`const`** fonction non membre sur un **`const`** objet.  Solutions possibles :

- Supprimez **`const`** de la déclaration de l’objet.

- Ajoutez **`const`** à la fonction membre.

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

Lors de la compilation avec **/CLR**, vous ne pouvez pas appeler une fonction sur un **`const`** **`volatile`** type managé qualifié ou. Vous ne pouvez pas déclarer une fonction membre const d’une classe managée, donc vous ne pouvez pas appeler des méthodes sur des objets managés const.

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
