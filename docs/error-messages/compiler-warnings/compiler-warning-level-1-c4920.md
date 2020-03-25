---
title: Avertissement du compilateur (niveau 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: b587a4ca2a78bc2ac54640adb2b149d97bef4def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174659"
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
