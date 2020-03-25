---
title: Avertissement du compilateur (niveau 3) C4073
ms.date: 11/04/2016
f1_keywords:
- C4073
helpviewer_keywords:
- C4073
ms.assetid: 50081a6e-6acd-45ff-8484-9b1ea926cc5c
ms.openlocfilehash: 80b43f5fc5af23d84fe43727b75d041e39405ade
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199108"
---
# <a name="compiler-warning-level-3-c4073"></a>Avertissement du compilateur (niveau 3) C4073

initialiseurs placés dans la zone d’initialisation de la bibliothèque

Seuls les développeurs de bibliothèques tierces doivent utiliser la zone d’initialisation de la bibliothèque, qui est spécifiée par [#pragma init_seg](../../preprocessor/init-seg.md). L’exemple suivant génère l’C4073 :

```cpp
// C4073.cpp
// compile with: /W3
#pragma init_seg(lib)   // C4073

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```
