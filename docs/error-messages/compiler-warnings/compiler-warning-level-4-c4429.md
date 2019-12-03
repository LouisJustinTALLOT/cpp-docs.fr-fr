---
title: Avertissement du compilateur (niveau 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: e814867278701be11b0158789f6373453aea75b8
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683238"
---
# <a name="compiler-warning-level-4-c4429"></a>Avertissement du compilateur (niveau 4) C4429

nom de caractère universel éventuellement incomplet ou incorrect

Le compilateur a détecté une séquence de caractères qui peut être un nom de caractère universel mal formé. Un nom de caractère universel est `\u` suivi de quatre chiffres hexadécimaux, ou `\U` suivi de huit chiffres hexadécimaux.

L’exemple suivant génère l’C4429 :

```cpp
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```