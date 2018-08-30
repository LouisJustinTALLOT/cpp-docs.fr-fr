---
title: Compilateur avertissement (niveau 1) C4326 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4326
dev_langs:
- C++
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cee18a9ccc807370cf2fb40748939f211a4ba52f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211002"
---
# <a name="compiler-warning-level-1-c4326"></a>Avertissement du compilateur (niveau 1) C4326

> type de retour de '*fonction*'doit être'*type1*« au lieu de »*type2*'

## <a name="remarks"></a>Notes

Une fonction a retourné un type autre que *type1*. Par exemple, à l’aide de [/Za](../../build/reference/za-ze-disable-language-extensions.md), **principal** n’a pas retourné un **int**.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4326 et montre comment la corriger :

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```