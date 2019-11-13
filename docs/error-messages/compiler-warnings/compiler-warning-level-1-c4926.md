---
title: Avertissement du compilateur (niveau 1) C4926
ms.date: 11/04/2016
f1_keywords:
- C4926
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
ms.openlocfilehash: a68e251209cb9664552b4324de108f2cf7ce3f37
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050216"
---
# <a name="compiler-warning-level-1-c4926"></a>Avertissement du compilateur (niveau 1) C4926

'identifier' : symbole déjà défini : attributs ignorés

Une déclaration anticipée a été trouvée, mais il existe déjà une construction avec attributs ayant le même nom. Les attributs de la déclaration anticipée sont ignorés.

L’exemple suivant génère l’erreur C4926 :

```cpp
// C4926.cpp
// compile with: /W1
[module(name="MyLib")];

[coclass]
struct a {
};

[coclass]
struct a;   // C4926

int main() {
}
```