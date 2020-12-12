---
description: 'En savoir plus sur : erreur du compilateur C2675'
title: Erreur du compilateur C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: 71d52a8da09861078811757ad7af7c757e418e5c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282027"
---
# <a name="compiler-error-c2675"></a>Erreur du compilateur C2675

'opérateur’unaire : 'type’ne définit pas cet opérateur ou une conversion vers un type acceptable pour l’opérateur prédéfini

C2675 peut également se produire lors de l’utilisation d’un opérateur unaire, et le type ne définit pas l’opérateur ou une conversion vers un type acceptable pour l’opérateur prédéfini. Pour utiliser l'opérateur, vous devez le surcharger pour le type spécifié ou définir une conversion vers un type pour lequel l'opérateur est défini.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2675.

```cpp
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```
