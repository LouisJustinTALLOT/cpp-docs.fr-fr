---
title: Avertissement du compilateur (niveau 4) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 2521366a9f33e8c5b1b7d41951a7cb08adfc2561
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199821"
---
# <a name="compiler-warning-level-1-c4216"></a>Avertissement du compilateur (niveau 4) C4216

extension non standard utilisée : float long

Les extensions Microsoft par défaut (/Ze) traitent la valeur **float long** comme **double**. Compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)). Utilisez **double** pour assurer la compatibilité. L’exemple suivant génère l’C4216 :

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```
