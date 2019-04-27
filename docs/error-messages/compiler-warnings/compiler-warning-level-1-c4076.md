---
title: Avertissement du compilateur (niveau 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 3a56e58d9bec1034a55f4e588dbddd0dba03f348
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208025"
---
# <a name="compiler-warning-level-1-c4076"></a>Avertissement du compilateur (niveau 1) C4076

> «*modificateur de type*' : ne peut pas être utilisé avec le type '*typename*»

## <a name="remarks"></a>Notes

Un modificateur de type, s’il s’agit **signé** ou **non signé**, ne peut pas être utilisé avec un type non entier. *modificateur de type* est ignoré.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement de C4076 ; Pour corriger ce problème, supprimez le **non signé** modificateur de type :

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```