---
title: Erreur du compilateur C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: aea79509d0e1ae5c31fcf0cf369c28af39a21154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367926"
---
# <a name="compiler-error-c2675"></a>Erreur du compilateur C2675

l’opérateur unaire 'opérateur' : 'type' ne définit pas cet opérateur ou une conversion vers un type acceptable pour l’opérateur prédéfini

C2675 peut également se produire lorsque vous utilisez un opérateur unaire, et le type ne définit pas l’opérateur ou une conversion vers un type acceptable pour l’opérateur prédéfini. Pour utiliser l'opérateur, vous devez le surcharger pour le type spécifié ou définir une conversion vers un type pour lequel l'opérateur est défini.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2675.

```
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