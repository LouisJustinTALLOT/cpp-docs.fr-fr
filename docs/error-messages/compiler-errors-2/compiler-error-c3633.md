---
description: 'En savoir plus sur : erreur du compilateur C3633'
title: Erreur du compilateur C3633
ms.date: 11/04/2016
f1_keywords:
- C3633
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
ms.openlocfilehash: caf89e2297bb4e9d62be76699b153f013095fa34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239257"
---
# <a name="compiler-error-c3633"></a>Erreur du compilateur C3633

Impossible de définir’Member’en tant que membre de’type’managé

Les membres de données de classe de référence CLR ne peuvent pas être d’un type C++ non POD.  Vous pouvez uniquement instancier un type natif POD dans un type CLR.  Par exemple, un type POD ne peut pas contenir un constructeur de copie ou un opérateur d’assignation.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3633.

```cpp
// C3633.cpp
// compile with: /clr /c
#pragma warning( disable : 4368 )

class A1 {
public:
   A1() { II = 0; }
   int II;
};

ref class B {
public:
   A1 a1;   // C3633
   A1 * a2;   // OK
   B() : a2( new A1 ) {}
    ~B() { delete a2; }
};
```
