---
title: Compilateur avertissement (niveau 4) C4514 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4514
dev_langs:
- C++
helpviewer_keywords:
- C4514
ms.assetid: cdae966a-9cd4-4e31-af30-2a014e68f614
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 936370a97463c11d6fcdf15d1856c1dd2b0b4335
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060874"
---
# <a name="compiler-warning-level-4-c4514"></a>Avertissement du compilateur (niveau 4) C4514

'fonction' : fonction inline non référencée a été supprimée.

L’optimiseur a supprimé une fonction inline qui n’est pas appelée.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’erreur C4514 :

```
// C4514.cpp
// compile with: /W4
#pragma warning(default : 4514)
class A
{
   public:
      void func()   // C4514, remove the function to resolve
      {
      }
};

int main()
{
}
```