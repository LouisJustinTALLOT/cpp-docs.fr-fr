---
description: 'En savoir plus sur : erreur du compilateur C2142'
title: Erreur du compilateur C2142
ms.date: 11/04/2016
f1_keywords:
- C2142
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
ms.openlocfilehash: 65bd189fe99bb54549e458b093b72d8e47b840a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235526"
---
# <a name="compiler-error-c2142"></a>Erreur du compilateur C2142

les déclarations de fonction diffèrent, les paramètres de variable spécifiés uniquement dans l’une d’entre elles

Une déclaration de la fonction contient une liste de paramètres de variables. Aucune autre déclaration. C ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) uniquement.

L’exemple suivant génère l’C2142 :

```c
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```
