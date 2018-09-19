---
title: Erreur du compilateur C2447 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2447
dev_langs:
- C++
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cc18c8e6ffb31de062957e16f6f3a6573379ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035134"
---
# <a name="compiler-error-c2447"></a>Erreur du compilateur C2447

'{' : en-tête de fonction manquant (liste formelle à l'ancien format ?)

Le compilateur a rencontré une accolade ouvrante inattendue au niveau de l'étendue globale. Dans la plupart des cas, cela est dû à un en-tête de fonction incorrect, une déclaration mal placée ou un point-virgule égaré. Pour résoudre ce problème, vérifiez que l'accolade ouvrante suit un en-tête de fonction correct, et qu'elle n'est pas précédée d'une déclaration ou d'un point-virgule égaré.

Cette erreur peut également être provoquée par une liste d'arguments formels en langage C à l'ancien format. Pour résoudre ce problème, refactorisez la liste d'arguments afin d'utiliser le style moderne, c'est-à-dire entre parenthèses.

L’exemple suivant génère C2447 :

```
// C2447.cpp
int c;
{}       // C2447
```