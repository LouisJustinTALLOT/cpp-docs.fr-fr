---
title: Erreur du compilateur C2055 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2055
dev_langs:
- C++
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6c63d79325417fbd9b1f451fb4a51f13957b4df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019340"
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