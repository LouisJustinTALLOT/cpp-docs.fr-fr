---
title: Compilateur avertissement (niveau 1) C4079
ms.date: 11/04/2016
f1_keywords:
- C4079
helpviewer_keywords:
- C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
ms.openlocfilehash: 8f9a9e05ab2a65ad954f9928f7b9fab0e7fee9cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207523"
---
# <a name="compiler-warning-level-1-c4079"></a>Compilateur avertissement (niveau 1) C4079

jeton 'token' inattendu

Un jeton séparateur inattendu se produit dans une liste d’arguments du pragma. Le reste du pragma a été ignoré.

L’exemple suivant génère l’erreur C4079 :

```
// C4079.cpp
// compile with: /W1
#pragma warning(disable : 4081)
#pragma pack(c,16)   // C4079

int main() {
}
```