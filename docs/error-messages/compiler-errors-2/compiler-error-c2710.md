---
description: 'En savoir plus sur : erreur du compilateur C2710'
title: Erreur du compilateur C2710
ms.date: 11/04/2016
f1_keywords:
- C2710
helpviewer_keywords:
- C2710
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
ms.openlocfilehash: ea9e4eaefa023362647f418be16a72ee14fbd044
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320855"
---
# <a name="compiler-error-c2710"></a>Erreur du compilateur C2710

'Construct' : ' __declspec (modifier) 'ne peut s’appliquer qu’à une fonction qui retourne un pointeur

Une fonction dont la valeur de retour est un pointeur est la seule construction à laquelle `modifier` peut être appliquée.

L’exemple suivant génère l’C2710 :

```cpp
// C2710.cpp
__declspec(restrict) void f();   // C2710
// try the following line instead
__declspec(restrict) int * g();
```
