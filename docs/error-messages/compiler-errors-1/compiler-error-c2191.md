---
description: 'En savoir plus sur : erreur du compilateur C2191'
title: Erreur du compilateur C2191
ms.date: 11/04/2016
f1_keywords:
- C2191
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
ms.openlocfilehash: b3b2133e70eeae566a972b0e5db11105b316d6f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337673"
---
# <a name="compiler-error-c2191"></a>Erreur du compilateur C2191

seconde liste de paramètres plus longue que la première

Une fonction C a été déclarée une deuxième fois avec une liste de paramètres plus longue. C ne prend pas en charge les fonctions surchargées.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2191 :

```c
// C2191.c
// compile with: /Za /c
void func( int );
void func( int, float );   // C2191 different parameter list
void func2( int, float );   // OK
```
