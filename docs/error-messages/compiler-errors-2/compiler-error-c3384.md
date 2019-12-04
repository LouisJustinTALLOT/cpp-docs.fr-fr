---
title: Erreur du compilateur C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: 059518462bd7a0463fd03fec6434acbbda7ee60a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756433"
---
# <a name="compiler-error-c3384"></a>Erreur du compilateur C3384

'type_parameter' : la contrainte de valeur et la contrainte ref s’excluent mutuellement

Vous ne pouvez pas contraindre un type générique à `value class` et `ref class`à la fois.

Pour plus d’informations, consultez [contraintesC++sur les paramètres de type générique (/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3384.

```cpp
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```
