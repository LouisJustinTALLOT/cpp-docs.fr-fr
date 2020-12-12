---
description: 'En savoir plus sur : erreur du compilateur C2379'
title: Erreur du compilateur C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: 4b278040107a026ffd5f7bee79e709519647cb54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174713"
---
# <a name="compiler-error-c2379"></a>Erreur du compilateur C2379

le nombre de paramètres formels a un type différent lors de sa promotion

Le type du paramètre spécifié n’est pas compatible, par le biais des promotions par défaut, avec le type dans une déclaration précédente. Il s’agit d’une erreur en C ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) et d’un avertissement avec les extensions Microsoft (**/Ze**).

L’exemple suivant génère l’C2379 :

```c
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```
