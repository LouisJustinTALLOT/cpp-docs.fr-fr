---
title: Avertissement du compilateur (niveau 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: cd501cf0e3b434523623276027056c93c77fc278
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393478"
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