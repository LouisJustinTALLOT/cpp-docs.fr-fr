---
description: 'En savoir plus sur : erreur du compilateur C2679'
title: Erreur du compilateur C2679
ms.date: 11/04/2016
f1_keywords:
- C2679
helpviewer_keywords:
- C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
ms.openlocfilehash: 3e2df2e54e729d2242bdc95a062f6c5dcf74f19d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177443"
---
# <a name="compiler-error-c2679"></a>Erreur du compilateur C2679

'opérateur’binaire : aucun opérateur trouvé qui accepte un opérande de partie droite de type’type' (ou il n’existe aucune conversion acceptable)

Pour utiliser l'opérateur, vous devez le surcharger pour le type spécifié ou définir une conversion vers un type pour lequel l'opérateur est défini.

L’exemple suivant génère l’C2679 :

```cpp
// C2679.cpp
class C {
public:
   C();   // no constructor with an int argument
} c;

class D {
public:
   D(int) {}
   D(){}
} d;

int main() {
   c = 10;   // C2679
   d = 10;   // OK
}
```
