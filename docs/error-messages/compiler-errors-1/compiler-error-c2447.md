---
description: 'En savoir plus sur : erreur du compilateur C2447'
title: Erreur du compilateur C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: c27846b002b3b58e3ed2e1dd89c06565b32d49b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189650"
---
# <a name="compiler-error-c2447"></a>Erreur du compilateur C2447

'{' : en-tête de fonction manquant (liste formelle à l'ancien format ?)

Le compilateur a rencontré une accolade ouvrante inattendue au niveau de l'étendue globale. Dans la plupart des cas, cela est dû à un en-tête de fonction incorrect, une déclaration mal placée ou un point-virgule égaré. Pour résoudre ce problème, vérifiez que l'accolade ouvrante suit un en-tête de fonction correct, et qu'elle n'est pas précédée d'une déclaration ou d'un point-virgule égaré.

Cette erreur peut également être provoquée par une liste d’arguments formels en langage C à l’ancien format. Pour résoudre ce problème, refactorisez la liste d'arguments afin d'utiliser le style moderne, c'est-à-dire entre parenthèses.

L’exemple suivant génère l’C2447 :

```cpp
// C2447.cpp
int c;
{}       // C2447
```
