---
description: 'En savoir plus sur : erreur du compilateur C3295'
title: Erreur du compilateur C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 55fab24088690f5d5bb92da0cc55442bcebeed01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144623"
---
# <a name="compiler-error-c3295"></a>Erreur du compilateur C3295

'#pragma pragma' ne peut être utilisé qu’au niveau de la portée globale ou de la portée espace de noms

Certains pragmas ne peuvent pas être utilisés dans une fonction.  Pour plus d’informations [, consultez directives pragma et le mot clé __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3295.

```cpp
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```
