---
description: 'En savoir plus sur : erreur du compilateur C3209'
title: Erreur du compilateur C3209
ms.date: 11/04/2016
f1_keywords:
- C3209
helpviewer_keywords:
- C3209
ms.assetid: 1de44e39-69d1-4894-8f89-ff92136e8e5d
ms.openlocfilehash: 81b2453a8e6318c082d6cd8838cc4a384ba80517
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173920"
---
# <a name="compiler-error-c3209"></a>Erreur du compilateur C3209

'classe' : la classe générique doit être une classe managée ou WinRTclass

Une classe générique doit être une classe managée ou une classe Windows Runtime.

L'exemple suivant génère l'erreur C3209 et montre comment la corriger :

```cpp
// C3209.cpp
// compile with: /clr
generic <class T>
class C {};   // C3209

// OK - ref class can be generic
generic <class T>
ref class D {};
```
