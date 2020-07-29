---
title: Avertissement du compilateur (niveau 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 1958aec4d6642188af1467ab4cab1ecf55c29165
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223315"
---
# <a name="compiler-warning-level-1-c4076"></a>Avertissement du compilateur (niveau 1) C4076

> '*modificateur de type*' : ne peut pas être utilisé avec le type'*TypeName*'

## <a name="remarks"></a>Notes

Un modificateur de type, qu’il soit **`signed`** ou **`unsigned`** , ne peut pas être utilisé avec un type non entier. le *modificateur de type* est ignoré.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4076 ; pour le résoudre, supprimez le **`unsigned`** modificateur de type :

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
