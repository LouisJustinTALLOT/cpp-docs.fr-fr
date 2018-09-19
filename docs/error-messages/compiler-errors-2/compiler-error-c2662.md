---
title: Erreur du compilateur C2662 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2662
dev_langs:
- C++
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e794f50dd6a23101e004618468b432c8969e54b5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042063"
---
# <a name="compiler-error-c2662"></a>Erreur du compilateur C2662

'fonction' : Impossible de convertir un pointeur 'this' de 'type1' en 'type2'

Le compilateur n’a pas pu convertir le `this` pointeur à partir de `type1` à `type2`.

Cette erreur peut être provoquée en appelant une non -`const` fonction membre sur un `const` objet.  Solutions possibles :

- Supprimer le `const` à partir de la déclaration de l’objet.

- Ajouter `const` à la fonction membre.

L’exemple suivant génère l’erreur C2662 :

```
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

Lors de la compilation avec **/CLR**, vous ne pouvez pas appeler une fonction sur un `const` ou `volatile` qualifié du type managé. Vous ne pouvez pas déclarer une fonction membre const d’une classe managée, afin que vous ne pouvez pas appeler des méthodes sur les objets gérés constantes.

```
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

L’exemple suivant génère l’erreur C2662 :

```
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