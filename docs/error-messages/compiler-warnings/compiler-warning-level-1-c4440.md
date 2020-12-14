---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4440'
title: Avertissement du compilateur (niveau 1) C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: 9e0a126ea1461e0b98bcef5117b893ea232fe262
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311043"
---
# <a name="compiler-warning-level-1-c4440"></a>Avertissement du compilateur (niveau 1) C4440

redéfinition de la Convention d’appel de’calling_convention1 'à’calling_convention2 'ignorée

Une tentative de modification de la Convention d’appel a été ignorée.

L’exemple suivant génère l’C4440 :

```cpp
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```
