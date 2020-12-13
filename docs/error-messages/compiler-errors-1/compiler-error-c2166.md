---
description: 'En savoir plus sur : erreur du compilateur C2166'
title: Erreur du compilateur C2166
ms.date: 11/04/2016
f1_keywords:
- C2166
helpviewer_keywords:
- C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
ms.openlocfilehash: 195782fca62b9bf69d17fa1aa382df2127b594e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145511"
---
# <a name="compiler-error-c2166"></a>Erreur du compilateur C2166

l-value définit un objet const

Le code tente de modifier un élément déclaré **`const`** .

L’exemple suivant génère l’erreur C2166 :

```cpp
// C2166.cpp
int f();
int main() {
   ( (const int&) 1 ) = 5;   // C2166
}
```
