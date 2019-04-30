---
title: Avertissement du compilateur (niveau 4) C4212
ms.date: 11/04/2016
f1_keywords:
- C4212
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
ms.openlocfilehash: 8eca942de1d2f78f5e42d4aac7e2441789a01862
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401161"
---
# <a name="compiler-warning-level-4-c4212"></a>Avertissement du compilateur (niveau 4) C4212

extension non standard utilisée : déclaration de fonction de points de suspension utilisés

Le prototype de fonction a un nombre variable d’arguments. La définition de fonction ne fait pas.

L’exemple suivant génère l’erreur C4212 :

```
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```