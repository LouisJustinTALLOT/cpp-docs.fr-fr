---
description: 'En savoir plus sur : erreur du compilateur C2055'
title: Erreur du compilateur C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 0692488b8e1ea91fe235ade512c5fbe5094cdaef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174934"
---
# <a name="compiler-error-c2055"></a>Erreur du compilateur C2055

liste de paramètres formels attendue, et non une liste de types

Une définition de fonction contient une liste de types de paramètres au lieu d’une liste de paramètres formels. ANSI C exige que les paramètres formels soient nommés, sauf s’ils sont void ou des points de suspension ( `...` ).

L’exemple suivant génère l’C2055 :

```c
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```
