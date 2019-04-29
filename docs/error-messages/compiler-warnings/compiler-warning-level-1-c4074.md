---
title: Compilateur avertissement (niveau 1) C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: d9b0259e95198396d8c34ca43781045248e22ad9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374740"
---
# <a name="compiler-warning-level-1-c4074"></a>Compilateur avertissement (niveau 1) C4074

initialiseurs placés dans une zone d’initialisation réservée par le compilateur

La zone d’initialisation du compilateur, qui est spécifiée par [#pragma init_seg](../../preprocessor/init-seg.md), est réservée par Microsoft. Le code dans cette zone peut être exécuté avant l’initialisation de la bibliothèque Runtime C.

L’exemple suivant génère l’erreur C4074 :

```
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```