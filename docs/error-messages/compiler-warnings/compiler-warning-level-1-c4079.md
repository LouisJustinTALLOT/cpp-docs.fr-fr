---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4079'
title: Avertissement du compilateur (niveau 1) C4079
ms.date: 11/04/2016
f1_keywords:
- C4079
helpviewer_keywords:
- C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
ms.openlocfilehash: d666d6d1272c1a131af5aa6b4e9248398e270758
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228662"
---
# <a name="compiler-warning-level-1-c4079"></a>Avertissement du compilateur (niveau 1) C4079

jeton 'token' inattendu

Un jeton de séparateur inattendu se produit dans une liste d’arguments pragma. Le reste du pragma a été ignoré.

L’exemple suivant génère l’C4079 :

```cpp
// C4079.cpp
// compile with: /W1
#pragma warning(disable : 4081)
#pragma pack(c,16)   // C4079

int main() {
}
```
