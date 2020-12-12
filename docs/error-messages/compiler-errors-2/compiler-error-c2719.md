---
description: 'En savoir plus sur : erreur du compilateur C2719'
title: Erreur du compilateur C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: 61e01107d5681c4bab39b06b00293ecdbeb9fc9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320720"
---
# <a name="compiler-error-c2719"></a>Erreur du compilateur C2719

'paramètre' : le paramètre formel avec __declspec(align('#')) ne sera pas aligné

Le [](../../cpp/align-cpp.md) **`__declspec`** modificateur align n’est pas autorisé sur les paramètres de fonction. L’alignement des paramètres de fonction est contrôlé par la convention d’appel utilisée. Pour plus d’informations, consultez [conventions d’appel](../../cpp/calling-conventions.md).

L'exemple suivant génère l'erreur C2719 et montre comment la corriger :

```cpp
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```
