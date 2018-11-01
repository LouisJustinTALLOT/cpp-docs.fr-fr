---
title: Erreur du compilateur C2736
ms.date: 11/04/2016
f1_keywords:
- C2736
helpviewer_keywords:
- C2736
ms.assetid: 95a6bc28-c0cb-49dc-87e6-e993dbbba881
ms.openlocfilehash: 7ce63c1e9d9e6ab04a7f7200c5b34f346100733b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658977"
---
# <a name="compiler-error-c2736"></a>Erreur du compilateur C2736

mot clé 'mot_clé' n’est pas autorisé dans un cast

Le mot clé n’est pas valide dans un cast.

L’exemple suivant génère l’erreur C2736 :

```
// C2736.cpp
int main() {
   return (virtual) 0;   // C2736
   // try the following line instead
   // return 0;
}
```