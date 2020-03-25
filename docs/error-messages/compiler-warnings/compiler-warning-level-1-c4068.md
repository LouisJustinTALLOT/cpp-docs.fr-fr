---
title: Avertissement du compilateur (niveau 1) C4068
ms.date: 11/04/2016
f1_keywords:
- C4068
helpviewer_keywords:
- C4068
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
ms.openlocfilehash: 9a19acd42836ed678c7e615e1606434f2572c187
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200237"
---
# <a name="compiler-warning-level-1-c4068"></a>Avertissement du compilateur (niveau 1) C4068

pragma inconnu

Le compilateur a ignoré un [pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)non reconnu. Vérifiez que le **pragma** est autorisé par le compilateur que vous utilisez. L’exemple suivant génère l’avertissement C4068 :

```cpp
// C4068.cpp
// compile with: /W1
#pragma NotAValidPragmaName   // C4068, use valid name to resolve
int main()
{
}
```
