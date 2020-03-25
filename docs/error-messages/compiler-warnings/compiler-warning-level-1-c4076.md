---
title: Avertissement du compilateur (niveau 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 77efeae27a67ea844759fd9980801d3daf788e89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200254"
---
# <a name="compiler-warning-level-1-c4076"></a>Avertissement du compilateur (niveau 1) C4076

> '*modificateur de type*' : ne peut pas être utilisé avec le type'*TypeName*'

## <a name="remarks"></a>Notes

Un modificateur de type, qu’il soit **signé** ou **non signé**, ne peut pas être utilisé avec un type non entier. le *modificateur de type* est ignoré.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4076 ; pour le résoudre, supprimez le modificateur de type **non signé** :

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
