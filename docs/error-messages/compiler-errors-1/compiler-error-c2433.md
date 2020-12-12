---
description: 'En savoir plus sur : erreur du compilateur C2433'
title: Erreur du compilateur C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: 67d7a0f34ef988c6d67a720a2af2d2fa493b2bf2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189949"
---
# <a name="compiler-error-c2433"></a>Erreur du compilateur C2433

'identificateur' : 'modificateur’non autorisé sur les déclarations de données

Les **`friend`** **`virtual`** **`inline`** modificateurs, et ne peuvent pas être utilisés pour les déclarations de données.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2433.

```cpp
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```
