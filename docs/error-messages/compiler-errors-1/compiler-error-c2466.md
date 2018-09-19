---
title: Erreur du compilateur C2466 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d43ee9d09fba77db022177a06c6ebe95c65ff79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037838"
---
# <a name="compiler-error-c2466"></a>Erreur du compilateur C2466

Impossible d’allouer un tableau de taille constante 0

Un tableau est alloué ou déclaré avec une taille égale à zéro. L’expression de constante pour la taille du tableau doit être un entier supérieur à zéro. Une déclaration de tableau avec un indice zéro est autorisée uniquement pour une classe, structure ou membre d’union et uniquement avec les extensions Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

L’exemple suivant génère l’erreur C2466 :

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```