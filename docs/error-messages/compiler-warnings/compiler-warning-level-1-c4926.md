---
title: Compilateur avertissement (niveau 1) C4926 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4926
dev_langs:
- C++
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1942c334f06dce7a8f208f01cae6e2da1b6bb6cf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087940"
---
# <a name="compiler-warning-level-1-c4926"></a>Avertissement du compilateur (niveau 1) C4926

'identifier' : symbole déjà défini : attributs ignorés

Une déclaration anticipée a été trouvée, mais il existe déjà une construction avec attributs ayant le même nom. Les attributs de la déclaration anticipée sont ignorés.

L’exemple suivant génère l’erreur C4926 :

```
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