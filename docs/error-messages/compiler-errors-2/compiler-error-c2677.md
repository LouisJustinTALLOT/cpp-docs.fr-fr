---
description: 'En savoir plus sur : erreur du compilateur C2677'
title: Erreur du compilateur C2677
ms.date: 11/04/2016
f1_keywords:
- C2677
helpviewer_keywords:
- C2677
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
ms.openlocfilehash: 6a7570fa972897658c9ffa81052148e9ce7cd6cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267805"
---
# <a name="compiler-error-c2677"></a>Erreur du compilateur C2677

'opérateur’binaire : aucun opérateur global trouvé qui accepte le type’type' (ou il n’existe aucune conversion acceptable)

Pour utiliser l'opérateur, vous devez le surcharger pour le type spécifié ou définir une conversion vers un type pour lequel l'opérateur est défini.

L’exemple suivant génère l’C2677 :

```cpp
// C2677.cpp
class C {
public:
   C(){}
} c;

class D {
public:
   D(){}
   operator int(){return 0;}
} d;

int main() {
   int i = 1 >> c;   // C2677
   int j = 1 >> d;   // OK operator int() defined
}
```
