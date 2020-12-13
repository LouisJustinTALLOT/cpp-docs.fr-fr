---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4326'
title: Avertissement du compilateur (niveau 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: d7c82d7a0157b53e60281bbe7c45a38cc765a73d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340044"
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
