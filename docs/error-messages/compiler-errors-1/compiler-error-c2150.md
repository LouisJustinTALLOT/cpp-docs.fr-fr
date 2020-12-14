---
description: 'En savoir plus sur : erreur du compilateur C2150'
title: Erreur du compilateur C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: 5a609edba74e2aee8e0d2a6275fa1ca40fafe5c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223514"
---
# <a name="compiler-error-c2150"></a>Erreur du compilateur C2150

> '*identificateur*' : le champ de bits doit être de type’int', 'signed int’ou’unsigned int'

Le type de base pour un champ de bits doit être **`int`** , **`signed int`** ou **`unsigned int`** .

## <a name="example"></a>Exemple

Cet exemple montre comment vous pouvez rencontrer C2150 et comment le résoudre :

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```
