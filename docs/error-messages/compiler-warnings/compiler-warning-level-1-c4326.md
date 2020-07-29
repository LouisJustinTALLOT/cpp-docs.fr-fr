---
title: Avertissement du compilateur (niveau 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: 41d8b271660ce0b6840e701ddac0f0538b265968
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196550"
---
# <a name="compiler-warning-level-1-c4326"></a>Avertissement du compilateur (niveau 1) C4326

> le type de retour de'*Function*'doit être'*type1*'au lieu de'*type2*'

## <a name="remarks"></a>Notes

Une fonction a retourné un type autre que *type1*. Par exemple, à l’aide de [/za](../../build/reference/za-ze-disable-language-extensions.md), **main** n’a pas retourné de **`int`** .

## <a name="example"></a>Exemple

L’exemple suivant génère l’opération C4326 et montre comment la corriger :

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```
