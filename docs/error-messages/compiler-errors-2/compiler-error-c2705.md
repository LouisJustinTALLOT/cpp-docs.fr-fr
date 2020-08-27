---
title: Erreur du compilateur C2705
description: Décrit l’erreur C2705 du compilateur Microsoft C/C++.
ms.date: 08/25/2020
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 40d0f70ee379f5d1347b7443817713a53e097f89
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898742"
---
# <a name="compiler-error-c2705"></a>Erreur du compilateur C2705

> '*étiquette*' : saut non conforme dans la portée’bloc de gestionnaire d’exceptions'

## <a name="remarks"></a>Notes

L’exécution passe à une étiquette dans un **`try`** / **`catch`** **`__try`** / **`__except`** bloc, ou **`__try`** / **`__finally`** . Le compilateur n’autorise pas ce comportement. Pour plus d’informations, consultez [gestion des exceptions](../../cpp/exception-handling-in-visual-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2705 :

```cpp
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```
