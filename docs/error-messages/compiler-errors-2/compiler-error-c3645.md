---
title: Erreur du compilateur C3645
ms.date: 11/04/2016
f1_keywords:
- C3645
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
ms.openlocfilehash: f733de6920e00f1f53c87884a7a334e575bceb06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500332"
---
# <a name="compiler-error-c3645"></a>Erreur du compilateur C3645

'fonction' : __clrcall ne peut pas être utilisé sur les fonctions compilées en code natif

La présence de certains mots clés dans une fonction entraînera la fonction être compilé en code natif.

## <a name="example"></a>Exemple

L’exemple suivant génère C3645.

```
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```