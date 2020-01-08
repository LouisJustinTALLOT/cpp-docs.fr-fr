---
title: Erreur du compilateur C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 9cb6e4d5891c5aefc9d66e7d70a5cd7685ccd393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302040"
---
# <a name="compiler-error-c2055"></a>Erreur du compilateur C2055

liste de paramètres formels attendue, et non une liste de types

Une définition de fonction contient une liste de types de paramètres au lieu d’une liste de paramètres formels. ANSI C exige que les paramètres formels soient nommés, sauf s’ils sont void ou des points de suspension (`...`).

L’exemple suivant génère l’C2055 :

```c
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```
