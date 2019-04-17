---
title: Erreur du compilateur C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: d1b7e1a69035df358cf84ad791f611928dab8b5a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773630"
---
# <a name="compiler-error-c3384"></a>Erreur du compilateur C3384

'type_parameter' : la contrainte de valeur et la contrainte ref s’excluent mutuellement

Vous ne pouvez pas contraindre un type générique à `value class` et `ref class`à la fois.

Consultez [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3384.

```
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```