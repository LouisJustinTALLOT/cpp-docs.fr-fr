---
title: Erreur du compilateur C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 20b08c0d2cd89224ed3d3b8b34915deb947b0b4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205112"
---
# <a name="compiler-error-c2483"></a>Erreur du compilateur C2483

>'*identificateur*' : un objet avec un constructeur ou un destructeur ne peut pas être déclaré’thread'

Ce message d’erreur est obsolète dans Visual Studio 2015 et versions ultérieures. Dans les versions précédentes, les variables déclarées avec l’attribut `thread` ne peuvent pas être initialisées avec un constructeur ou une autre expression qui requiert une évaluation au moment de l’exécution. Une expression statique est requise pour initialiser `thread` données.

## <a name="example"></a>Exemple

L’exemple suivant génère C2483 dans Visual Studio 2013 et les versions antérieures.

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
