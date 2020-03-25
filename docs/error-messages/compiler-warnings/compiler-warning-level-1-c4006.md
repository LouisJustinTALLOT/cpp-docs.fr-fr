---
title: Avertissement du compilateur (niveau 1) C4006
ms.date: 11/04/2016
f1_keywords:
- C4006
helpviewer_keywords:
- C4006
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
ms.openlocfilehash: b589a4bd6b9e14ec926f634f12883e02bf450514
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164714"
---
# <a name="compiler-warning-level-1-c4006"></a>Avertissement du compilateur (niveau 1) C4006

\#undef attendait un identificateur

La directive `#undef` n’a pas spécifié d’identificateur dont il faut annuler la définition. La directive est ignorée. Pour éviter cet avertissement, spécifiez un identificateur. L’exemple suivant génère l’avertissement C4006 :

```cpp
// C4006.cpp
// compile with: /W1
#undef   // C4006

// try..
// #undef TEST

int main() {
}
```
