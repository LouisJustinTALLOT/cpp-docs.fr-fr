---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4302'
title: Avertissement du compilateur (niveau 2) C4302
ms.date: 11/04/2016
f1_keywords:
- C4302
helpviewer_keywords:
- C4302
ms.assetid: f5e1c939-e134-4cca-ba1e-9b15a81549ae
ms.openlocfilehash: 0be91208d62c06882713d6b00358665f518103fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173556"
---
# <a name="compiler-warning-level-2-c4302"></a>Avertissement du compilateur (niveau 2) C4302

'conversion' : troncation de’type 1 'à’type 2 '

Le compilateur a détecté une conversion d’un type plus grand en un type plus petit. Les informations peuvent être perdues.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4302 :

```cpp
// C4302.cpp
// compile with: /W2
#pragma warning(default : 4302)
int main() {
   int i;
   char c = (char) &i;     // C4302
   short s = (short) &i;   // C4302
}
```
