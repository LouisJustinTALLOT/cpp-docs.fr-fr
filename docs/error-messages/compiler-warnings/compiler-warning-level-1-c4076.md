---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4076'
title: Avertissement du compilateur (niveau 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 0bae49d3af23e499851fbf70fb24fdeb817ee03c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198256"
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
