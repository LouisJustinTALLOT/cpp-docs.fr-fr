---
title: Erreur irrécupérable C1190
ms.date: 11/04/2016
f1_keywords:
- C1190
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
ms.openlocfilehash: 8bd0332770dd0771ac7a02574185a506cf6fd416
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621336"
---
# <a name="fatal-error-c1190"></a>Erreur irrécupérable C1190

le code ciblé managé requiert une option '/clr'

Vous utilisez des constructions CLR, mais vous n’avez pas spécifié **/clr**.

Pour plus d'informations, consultez [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

L’exemple suivant génère l’erreur C1190 :

```
// C1190.cpp
// compile with: /c
__gc class A {};   // C1190
ref class A {};
```