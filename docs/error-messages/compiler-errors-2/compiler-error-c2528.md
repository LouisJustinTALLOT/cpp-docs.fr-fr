---
description: 'En savoir plus sur : erreur du compilateur C2528'
title: Erreur du compilateur C2528
ms.date: 11/04/2016
f1_keywords:
- C2528
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
ms.openlocfilehash: de07867f48843be76ff5b8d74dda9725b50a2560
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302177"
---
# <a name="compiler-error-c2528"></a>Erreur du compilateur C2528

'nom' : pointeur non conforme vers la référence

Vous ne pouvez pas déclarer un pointeur vers une référence. Déréférencez la variable avant de déclarer un pointeur vers celle-ci.

L’exemple suivant génère l’C2528 :

```cpp
// C2528.cpp
int i;
int &ir = i;
int & (*irptr) = ir;    // C2528
```
