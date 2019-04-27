---
title: Avertissement du compilateur (niveau 1) C4068
ms.date: 11/04/2016
f1_keywords:
- C4068
helpviewer_keywords:
- C4068
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
ms.openlocfilehash: 1e0cb7229733e15afd87548a1b18b3f58a64c239
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160852"
---
# <a name="compiler-warning-level-1-c4068"></a>Avertissement du compilateur (niveau 1) C4068

pragma inconnu

Le compilateur a ignoré un [pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)non reconnu. Vérifiez que le **pragma** est autorisé par le compilateur que vous utilisez. L’exemple suivant génère l’avertissement C4068 :

```
// C4068.cpp
// compile with: /W1
#pragma NotAValidPragmaName   // C4068, use valid name to resolve
int main()
{
}
```