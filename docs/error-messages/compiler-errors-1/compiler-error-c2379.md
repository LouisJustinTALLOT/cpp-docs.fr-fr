---
title: Erreur du compilateur C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: f096791a6120023e079b93452a4b35c669db2139
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302105"
---
# <a name="compiler-error-c2379"></a>Erreur du compilateur C2379

le nombre de paramètres formels a un type différent lors de sa promotion

Le type du paramètre spécifié n’est pas compatible, par le biais des promotions par défaut, avec le type dans une déclaration précédente. Il s’agit d’une erreur en C ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) et d’un avertissement avec les extensions Microsoft ( **/Ze**).

L’exemple suivant génère l’C2379 :

```c
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```
