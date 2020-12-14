---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4429'
title: Avertissement du compilateur (niveau 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: dbd552eb2f8e021f8bf7b7747e2a8aee49bb05a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241363"
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
