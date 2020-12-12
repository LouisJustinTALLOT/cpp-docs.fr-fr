---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4189'
title: Avertissement du compilateur (niveau 4) C4189
ms.date: 11/04/2016
f1_keywords:
- C4189
helpviewer_keywords:
- C4189
ms.assetid: 7ad9242c-228e-4054-8244-5e914b618ef3
ms.openlocfilehash: c5791325e0dc35ec501e1f4ff8593d620189ad89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173361"
---
# <a name="compiler-warning-level-4-c4189"></a>Avertissement du compilateur (niveau 4) C4189

'identificateur' : variable locale initialisée mais non référencée

Une variable est déclarée et initialisée, mais n’est pas utilisée.

L’exemple suivant génère l’avertissement C4189 :

```cpp
// C4189.cpp
// compile with: /W4
int main() {
   int a = 1;   // C4189, remove declaration to resolve
}
```
