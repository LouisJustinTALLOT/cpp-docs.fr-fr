---
title: Erreur du compilateur C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: 08ad1d09cb9149811566f67a585a718340254de9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635393"
---
# <a name="compiler-error-c3625"></a>Erreur du compilateur C3625

'type_natif' : un type natif ne peut pas dériver d'un type managé ou WinRT 'type'

Une classe native ne peut pas hériter d'une classe managée ou WinRT. Pour plus d’informations, consultez [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3625 :

```
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
