---
title: Erreur du compilateur C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 3c198168b4445e619148e5611621fa3ddba95d6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408785"
---
# <a name="compiler-error-c2055"></a>Erreur du compilateur C2055

liste de paramètres formels attendue, non une liste de type

Une définition de fonction contient une liste de type de paramètre au lieu d’une liste de paramètres formels. C ANSI requiert des paramètres formels à nommer, sauf si elles sont void ou des points de suspension (`...`).

L’exemple suivant génère l’erreur C2055 :

```
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```