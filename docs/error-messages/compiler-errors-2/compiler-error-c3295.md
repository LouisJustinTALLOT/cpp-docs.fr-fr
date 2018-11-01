---
title: Erreur du compilateur C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 63739989d737527e3f136bb3aac2269eda6231c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601693"
---
# <a name="compiler-error-c3295"></a>Erreur du compilateur C3295

'#pragma pragma' ne peut être utilisé qu’au niveau de la portée globale ou de la portée espace de noms

Certains pragmas ne peuvent pas être utilisés dans une fonction.  Consultez [Directives Pragma et mot clé _pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3295.

```
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```