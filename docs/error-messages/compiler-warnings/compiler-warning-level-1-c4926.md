---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4926'
title: Avertissement du compilateur (niveau 1) C4926
ms.date: 11/04/2016
f1_keywords:
- C4926
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
ms.openlocfilehash: 9b4f1d86085a5e0560237378728c2f267c44c780
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301891"
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
