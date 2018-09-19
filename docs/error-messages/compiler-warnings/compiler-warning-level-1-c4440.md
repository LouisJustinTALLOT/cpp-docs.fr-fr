---
title: Compilateur avertissement (niveau 1) C4440 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4440
dev_langs:
- C++
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e91479ee3e6562338a18ca482c319acb0e1647ca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088330"
---
# <a name="compiler-warning-level-1-c4440"></a>Avertissement du compilateur (niveau 1) C4440

appel de redéfinition de la convention de 'convention_appel1' en 'convention_appel2' ignoré

Une tentative de modification de la convention d’appel a été ignorée.

L’exemple suivant génère l’erreur C4440 :

```
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```