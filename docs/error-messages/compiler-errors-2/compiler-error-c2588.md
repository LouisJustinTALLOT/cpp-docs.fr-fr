---
title: Erreur du compilateur C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: f1f73e2585606e7e86213607a96ef713345419c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755406"
---
# <a name="compiler-error-c2588"></a>Erreur du compilateur C2588

' :: ~ identificateur' : destructeur global non conforme

Le destructeur est défini pour autre chose qu’une classe, une structure ou une Union. Cela n'est pas autorisé.

Cette erreur peut être due à un nom de classe, de structure ou d’Union manquant sur le côté gauche de l’opérateur de résolution de portée (`::`).

L’exemple suivant génère l’C2588 :

```cpp
// C2588.cpp
~F();   // C2588
```
