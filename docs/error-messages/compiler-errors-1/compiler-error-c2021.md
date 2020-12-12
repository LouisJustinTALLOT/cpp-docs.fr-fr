---
description: 'En savoir plus sur : erreur du compilateur C2021'
title: Erreur du compilateur C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 823d9c3d42f1df7bc6f6f398dafd804daef76110
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175636"
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
