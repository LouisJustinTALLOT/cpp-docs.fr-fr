---
title: Compilateur avertissement (niveau 2) C4285 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4285
dev_langs:
- C++
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27ad828e25f647bddcc8a9ebe9662e2ba61f48d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040689"
---
# <a name="compiler-warning-level-2-c4285"></a>Avertissement du compilateur (niveau 2) C4285

type de retour de 'identifier::operator ->' est récurrent si appliqué à l’aide de la notation infixe

Spécifié **operator -> ()** fonction ne peut pas retourner le type pour lequel elle est définie ou une référence au type pour lequel il est défini.

L’exemple suivant génère l’erreur C4285 :

```
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```