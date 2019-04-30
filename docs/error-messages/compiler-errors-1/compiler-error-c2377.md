---
title: Erreur du compilateur C2377
ms.date: 11/04/2016
f1_keywords:
- C2377
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
ms.openlocfilehash: b4789469fe27dafb2fb13bf3db085958db8d1478
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393725"
---
# <a name="compiler-error-c2377"></a>Erreur du compilateur C2377

'identificateur' : redéfinition ; un typedef ne peut pas être surchargé avec un autre symbole

Un identificateur `typedef` est redéfini.

L’exemple suivant génère l’erreur C2377 :

```
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```