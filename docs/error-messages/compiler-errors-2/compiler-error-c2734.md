---
description: 'En savoir plus sur : erreur du compilateur C2734'
title: Erreur du compilateur C2734
ms.date: 11/04/2016
f1_keywords:
- C2734
helpviewer_keywords:
- C2734
ms.assetid: e53a77b7-825c-42d1-a655-90e1c93b833e
ms.openlocfilehash: c867ef8456be35d0e566056aedc4de43d16c8f14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123173"
---
# <a name="compiler-error-c2734"></a>Erreur du compilateur C2734

'identificateur' : l’objet const doit être initialisé s’il n’est pas externe

L’identificateur est déclaré **`const`** mais non initialisé ou **`extern`** .

L’exemple suivant génère l’C2734 :

```cpp
// C2734.cpp
const int j;   // C2734
extern const int i;   // OK, declared as extern
```
