---
description: 'En savoir plus sur : erreur du compilateur C2464'
title: Erreur du compilateur C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: 2e30166529616809478927dbfe6ff1f1efb3002a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341839"
---
# <a name="compiler-error-c2464"></a>Erreur du compilateur C2464

'identificateur' : impossible d’utiliser’New’pour allouer une référence

Un identificateur de référence a été alloué avec l' **`new`** opérateur. Les références ne sont pas des objets de mémoire **`new`** . par conséquent, ne peut pas retourner un pointeur vers ces objets. Utilisez la syntaxe de déclaration de variable standard pour déclarer une référence.

L’exemple suivant génère l’C2464 :

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
