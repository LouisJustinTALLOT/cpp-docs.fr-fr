---
description: 'En savoir plus sur : erreur du compilateur C2483'
title: Erreur du compilateur C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 5edafbbb0852eb622f34698421ce9a2b794f9209
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123875"
---
# <a name="compiler-error-c2483"></a>Erreur du compilateur C2483

>'*identificateur*' : un objet avec un constructeur ou un destructeur ne peut pas être déclaré’thread'

Ce message d’erreur est obsolète dans Visual Studio 2015 et versions ultérieures. Dans les versions précédentes, les variables déclarées avec l' `thread` attribut ne peuvent pas être initialisées avec un constructeur ou une autre expression qui requiert une évaluation au moment de l’exécution. Une expression statique est requise pour initialiser les `thread` données.

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
