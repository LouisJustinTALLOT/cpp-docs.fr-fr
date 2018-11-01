---
title: Erreur du compilateur C2479
ms.date: 11/04/2016
f1_keywords:
- C2479
helpviewer_keywords:
- C2479
ms.assetid: c74c7869-e65b-4ca1-b6fa-eb39fed4458a
ms.openlocfilehash: 8b3b226ccbe42ec88ed92c64b97256d80a983254
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611430"
---
# <a name="compiler-error-c2479"></a>Erreur du compilateur C2479

'identificateur' : 'allocate ()' est uniquement valide pour les éléments de données d’étendue static

Le `__declspec( allocate())` syntaxe peut être utilisée pour les données statiques uniquement.

L’exemple suivant génère l’erreur C2479 :

```
// C2479.cpp
// compile with: /c
#pragma section("mycode", read)
static __declspec(allocate("mycode")) void DoNothing() {}   // C2479
__declspec(allocate("mycode"))  int i = 0;   // OK
```