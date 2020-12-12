---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4616'
title: Avertissement du compilateur (niveau 1) C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: 55ddc805c12cdc33947ca1f76c744610a5650497
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208695"
---
# <a name="compiler-warning-level-1-c4616"></a>Avertissement du compilateur (niveau 1) C4616

\#pragma warning : le numéro d’avertissement’Number’n’est pas un avertissement de compilateur valide

Le numéro d’avertissement spécifié dans le pragma d' [Avertissement](../../preprocessor/warning.md) ne peut pas être réassigné. Le pragma a été ignoré.

L’exemple suivant génère l’C4616 :

```cpp
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```
