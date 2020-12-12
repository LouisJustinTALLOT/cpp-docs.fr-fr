---
description: 'En savoir plus sur : erreur du compilateur C2372'
title: Erreur du compilateur C2372
ms.date: 03/23/2020
f1_keywords:
- C2372
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
ms.openlocfilehash: 9cf94e63e673ca226f3f9c3f1b4c3aa0a6bf8016
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174908"
---
# <a name="compiler-error-c2372"></a>Erreur du compilateur C2372

> '*identificateur*' : redéfinition ; différents types d’indirection

L’identificateur est déjà défini avec un autre type dérivé.

L’exemple suivant génère l’C2372 :

```cpp
// C2372.cpp
// compile with: /c
extern int *fp;
extern int fp[];   // C2372
extern int fp2[];   // OK
```
