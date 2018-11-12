---
title: Erreur du compilateur C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: d635601fbf8b36218fb47c09444f3f5d023c823e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653113"
---
# <a name="compiler-error-c2719"></a>Erreur du compilateur C2719

'paramètre' : le paramètre formel avec __declspec(align('#')) ne sera pas aligné

Le [aligner](../../cpp/align-cpp.md) `__declspec` modificateur n’est pas autorisé sur les paramètres de fonction. L’alignement des paramètres de fonction est contrôlé par la convention d’appel utilisée. Pour plus d’informations, consultez [Conventions d’appel](../../cpp/calling-conventions.md).

L'exemple suivant génère l'erreur C2719 et montre comment la corriger :

```
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```