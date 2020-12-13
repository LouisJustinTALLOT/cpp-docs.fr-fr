---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4740'
title: Avertissement du compilateur (niveau 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 31c25660177931e468681f3e563a9885ca1faa01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330529"
---
# <a name="compiler-warning-level-4-c4740"></a>Avertissement du compilateur (niveau 4) C4740

l’entrée ou la sortie du code ASM Inline supprime l’optimisation globale

Lorsqu’il y a un saut dans ou hors d’un **`asm`** bloc, les optimisations globales sont désactivées pour cette fonction.

L’exemple suivant génère l’C4740 :

```cpp
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```
