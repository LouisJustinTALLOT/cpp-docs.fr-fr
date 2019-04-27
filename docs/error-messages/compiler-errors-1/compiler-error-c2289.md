---
title: Erreur du compilateur C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 9fe9b765af72a8864e3e899cafcf648a9facb67e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182793"
---
# <a name="compiler-error-c2289"></a>Erreur du compilateur C2289

même qualificateur de type utilisé plusieurs fois

Une définition ou déclaration de type utilise un qualificateur de type (`const`, `volatile`, `signed`ou `unsigned`) plusieurs fois, ce qui crée une erreur de compatibilité ANSI (**/Za**).

L’exemple suivant génère l’erreur C2286 :

```
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```