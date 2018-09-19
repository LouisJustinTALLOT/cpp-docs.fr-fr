---
title: Erreur du compilateur C2379 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2379
dev_langs:
- C++
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec340a5a48705eb91bf5bf72ec20ad382f4b262c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032443"
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