---
title: Erreur du compilateur C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 24463abcf123fda285356c86e3394d7274f2f6c8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751038"
---
# <a name="compiler-error-c2021"></a>Erreur du compilateur C2021

valeur d’exposant attendue, non 'caractère'

Le caractère utilisé comme exposant d’une constante à virgule flottante n’est pas un nombre valide. Veillez à utiliser un exposant qui se trouve dans la plage.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2021 :

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>Exemple

Solution possible :

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```
