---
title: Avertissement du compilateur (niveau 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 96e1077ce3c9e60823a11aa41719738265ee703b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535978"
---
# <a name="compiler-warning-level-2-c4285"></a>Avertissement du compilateur (niveau 2) C4285

type de retour de 'identifier::operator ->' est récurrent si appliqué à l’aide de la notation infixe

Spécifié **operator -> ()** fonction ne peut pas retourner le type pour lequel elle est définie ou une référence au type pour lequel il est défini.

L’exemple suivant génère l’erreur C4285 :

```
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```