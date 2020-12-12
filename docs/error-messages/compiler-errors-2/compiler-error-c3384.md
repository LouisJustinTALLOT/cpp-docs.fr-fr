---
description: 'En savoir plus sur : erreur du compilateur C3384'
title: Erreur du compilateur C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: 79d5aabf185702c3d85485744b14e714a32aa76b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285576"
---
# <a name="compiler-error-c3384"></a>Erreur du compilateur C3384

'type_parameter' : la contrainte de valeur et la contrainte ref s’excluent mutuellement

Vous ne pouvez pas contraindre un type générique à **`value class`** et à **`ref class`** .

Pour plus d’informations, consultez [contraintes sur les paramètres de type générique (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

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
