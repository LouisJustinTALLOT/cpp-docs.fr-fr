---
title: Avertissement du compilateur (niveau 4) C4212
ms.date: 11/04/2016
f1_keywords:
- C4212
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
ms.openlocfilehash: d33e5c60bac657060ffef2a43686a5f737eb11cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161306"
---
# <a name="compiler-warning-level-4-c4212"></a>Avertissement du compilateur (niveau 4) C4212

extension non standard utilisée : points de suspension utilisés par la déclaration de fonction

Le prototype de fonction a un nombre variable d’arguments. La définition de la fonction ne le fait pas.

L’exemple suivant génère l’C4212 :

```c
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```
