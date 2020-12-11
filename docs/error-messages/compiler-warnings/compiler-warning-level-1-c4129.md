---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4129'
title: Avertissement du compilateur (niveau 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: 27ae487016a5d9a60a95e4715261ec5ba9171db4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155278"
---
# <a name="compiler-warning-level-1-c4129"></a>Avertissement du compilateur (niveau 1) C4129

'caractère' : séquence d’échappement de caractère non reconnue

La `character` barre oblique inverse suivante ( \\ ) dans une constante caractère ou chaîne n’est pas reconnue comme une séquence d’échappement valide. La barre oblique inverse est ignorée et n’est pas imprimée. Le caractère qui suit la barre oblique inverse est imprimé.

Pour imprimer une seule barre oblique inverse, spécifiez une double barre oblique inverse ( \\ \\ ).

La norme C++, dans la section 2.13.2, présente les séquences d’échappement.

L’exemple suivant génère l’C4129 :

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```
