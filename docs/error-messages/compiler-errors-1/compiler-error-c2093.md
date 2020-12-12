---
description: 'En savoir plus sur : erreur du compilateur C2093'
title: Erreur du compilateur C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d08c2e29415363fc64309a89691ec0852ca5fa88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251854"
---
# <a name="compiler-error-c2093"></a>Erreur du compilateur C2093

'Variable1 ' : ne peut pas être initialisé à l’aide de l’adresse de la variable automatique’portée2 '

Lors de la compilation avec [/za](../../build/reference/za-ze-disable-language-extensions.md), le programme a tenté d’utiliser l’adresse d’une variable automatique comme initialiseur.

L’exemple suivant génère l’C2093 :

```c
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```
