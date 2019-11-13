---
title: Avertissement du compilateur (niveau 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: 7cbb29c8dae24a87fcd5a32b4cf46d7a8ac4c790
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050241"
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

```cpp
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```