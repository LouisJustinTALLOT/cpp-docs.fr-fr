---
title: Compilateur avertissement (niveau 1) C4920 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4920
dev_langs:
- C++
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4873fcb1e5bb6d712e44b86d6f60589d6c8ddf4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091736"
---
# <a name="compiler-warning-level-1-c4920"></a>Avertissement du compilateur (niveau 1) C4920

enum enum membre membre=valeur déjà rencontré dans enum enum comme membre=valeur

Si une .tlb que vous passez à #import possède un même symbole défini dans deux enums ou plus, cet avertissement indique que les symboles identiques suivants seront ignorés et commentés dans le fichier .tlh.

Imaginez qu’une .tlb contienne :

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

Les exemples suivants génèrent l’avertissement C4920 :

```
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```