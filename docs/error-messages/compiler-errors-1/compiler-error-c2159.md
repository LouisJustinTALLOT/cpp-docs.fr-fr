---
description: 'En savoir plus sur : erreur du compilateur C2159'
title: Erreur du compilateur C2159
ms.date: 11/04/2016
f1_keywords:
- C2159
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
ms.openlocfilehash: 045515ba964832de8821e048eac58b0ec507d830
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181213"
---
# <a name="compiler-error-c2159"></a>Erreur du compilateur C2159

plus d'une classe de stockage spécifiée

Une déclaration contient plusieurs classes de stockage.

L’exemple suivant génère l’erreur C2159 :

```cpp
// C2159.cpp
// compile with: /c
static int i;   // OK
extern static int i;   // C2159
```
