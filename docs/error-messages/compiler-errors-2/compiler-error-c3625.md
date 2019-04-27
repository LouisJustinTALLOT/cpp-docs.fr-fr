---
title: Erreur du compilateur C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: a3c69b05e22c2d267ad07f19a0d0ab60f3eebb94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221864"
---
# <a name="compiler-error-c3625"></a>Erreur du compilateur C3625

'type_natif' : un type natif ne peut pas dériver d'un type managé ou WinRT 'type'

Une classe native ne peut pas hériter d'une classe managée ou WinRT. Pour plus d’informations, consultez [les Classes et Structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3625 :

```
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
