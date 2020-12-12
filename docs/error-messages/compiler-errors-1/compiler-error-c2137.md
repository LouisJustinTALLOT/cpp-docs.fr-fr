---
description: 'En savoir plus sur : erreur du compilateur C2137'
title: Erreur du compilateur C2137
ms.date: 11/04/2016
f1_keywords:
- C2137
helpviewer_keywords:
- C2137
ms.assetid: 984687ee-7766-4f6b-ae15-0c9a010e2366
ms.openlocfilehash: 053c933b3ee650d1d49c230d9bfc23c656f9a709
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323075"
---
# <a name="compiler-error-c2137"></a>Erreur du compilateur C2137

constante caractère vide

La constante caractère vide (' ') n’est pas autorisée.

L’exemple suivant génère l’erreur C2137 :

```cpp
// C2137.cpp
int main() {
   char c = '';   // C2137
   char d = ' ';   // OK
}
```
