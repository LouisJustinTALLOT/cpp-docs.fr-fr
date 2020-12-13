---
description: 'En savoir plus sur : erreur du compilateur C2197'
title: Erreur du compilateur C2197
ms.date: 11/04/2016
f1_keywords:
- C2197
helpviewer_keywords:
- C2197
ms.assetid: 6dd5a6ec-bc80-41b9-a4ac-46f80eaca42d
ms.openlocfilehash: a82a39eba23cae617cf910101f5550fd0f9f0ad4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341917"
---
# <a name="compiler-error-c2197"></a>Erreur du compilateur C2197

'function' : trop d’arguments pour un appel

Le compilateur a détecté un nombre trop élevé de paramètres pour un appel à la fonction ou une déclaration de fonction incorrecte.

L’exemple suivant génère l’erreur C2197 :

```c
// C2197.c
// compile with: /Za /c
void func( int );
int main() {
   func( 1, 2 );   // C2197 two actual parameters
   func( 2 );   // OK
}
```
