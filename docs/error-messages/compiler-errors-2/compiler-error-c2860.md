---
title: Erreur du compilateur C2860
ms.date: 11/04/2016
f1_keywords:
- C2860
helpviewer_keywords:
- C2860
ms.assetid: ccc83553-90ed-4e94-b5e9-38b58ae38e31
ms.openlocfilehash: 7d468fb2a71ce23bcd527cb02663dd5f7b7eecad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302863"
---
# <a name="compiler-error-c2860"></a>Erreur du compilateur C2860

'void' ne peut pas être un type d’argument, à l’exception de '(void)'

Type `void` ne peut pas être utilisé comme type d’argument avec d’autres arguments.

L’exemple suivant génère l’erreur C2860 :

```
// C2860.cpp
// compile with: /c
void profunc1(void, int i);   // C2860
void func10(void);   // OK
```