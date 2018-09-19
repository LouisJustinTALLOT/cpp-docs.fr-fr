---
title: Erreur du compilateur C2198 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2198
dev_langs:
- C++
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a4e391f35a4487246ca074d218391348c83e0d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096819"
---
# <a name="compiler-error-c2198"></a>Erreur du compilateur C2198

'function' : pas assez d’arguments pour un appel

Le compilateur a détecté un nombre insuffisant de paramètres pour un appel à la fonction, ou une déclaration de fonction incorrecte.

L’exemple suivant génère l’erreur C2198 :

```
// C2198.c
// compile with: /c
void func( int, int );
int main() {
   func( 1 );   // C2198 only one actual parameter
   func( 1, 1 );   // OK
}
```