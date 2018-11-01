---
title: Erreur du compilateur C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: d1a5632328c00ca2dcd03519d03fbdb648776a51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637877"
---
# <a name="compiler-error-c2483"></a>Erreur du compilateur C2483

>«*identificateur*' : objet avec un constructeur ou un destructeur ne peut pas être déclaré 'thread'

Ce message d’erreur est obsolète dans Visual Studio 2015 et versions ultérieures. Dans les versions précédentes, les variables déclarées avec le `thread` attribut ne peut pas être initialisé avec un constructeur ou une autre expression qui requiert une évaluation de l’exécution. Une expression statique est requise pour initialiser `thread` données.

## <a name="example"></a>Exemple

L’exemple suivant génère C2483 dans Visual Studio 2013 et versions antérieures.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Voir aussi

[thread](../../cpp/thread.md)