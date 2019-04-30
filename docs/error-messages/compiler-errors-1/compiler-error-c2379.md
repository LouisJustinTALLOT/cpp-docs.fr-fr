---
title: Erreur du compilateur C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: 1b3256efb6c0ff8236ba80a9ac681780f34fa8dd
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345646"
---
# <a name="compiler-error-c2379"></a>Erreur du compilateur C2379

nombre de paramètres formels a un type différent lors de sa promotion

Le type du paramètre spécifié n’est pas compatible, par le biais des promotions par défaut, avec le type dans une déclaration précédente. Il s’agit d’une erreur en C ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) et un avertissement avec les extensions Microsoft (**/Ze**).

L’exemple suivant génère C2379 :

```
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```