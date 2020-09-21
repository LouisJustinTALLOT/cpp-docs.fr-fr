---
title: Erreur du compilateur C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 97d1776bb3b29b3691ae31bb060410a83d581e2d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743293"
---
# <a name="compiler-error-c2021"></a>Erreur du compilateur C2021

valeur d’exposant attendue, non 'caractère'

Le caractère utilisé comme exposant d’une constante à virgule flottante n’est pas un nombre valide. Veillez à utiliser un exposant qui se trouve dans la plage.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2021 :

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

Solution possible :

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```
