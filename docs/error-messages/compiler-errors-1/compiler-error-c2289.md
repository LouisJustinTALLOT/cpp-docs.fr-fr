---
description: 'En savoir plus sur : erreur du compilateur C2289'
title: Erreur du compilateur C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: ba9af908af6defaccd6825ce3dad412ad6914c77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185958"
---
# <a name="compiler-error-c2289"></a>Erreur du compilateur C2289

même qualificateur de type utilisé plusieurs fois

Une déclaration ou une définition de type utilise un qualificateur de type ( **`const`** , **`volatile`** , **`signed`** ou **`unsigned`** ) plusieurs fois, ce qui provoque une erreur sous compatibilité ANSI (**/za**).

L’exemple suivant génère l’erreur C2286 :

```cpp
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```
