---
description: 'En savoir plus sur : erreur du compilateur C3625'
title: Erreur du compilateur C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: ee28175eac35e05ca2a4620dffa84cf995e053a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144493"
---
# <a name="compiler-error-c3625"></a>Erreur du compilateur C3625

'type_natif' : un type natif ne peut pas dériver d'un type managé ou WinRT 'type'

Une classe native ne peut pas hériter d'une classe managée ou WinRT. Pour plus d’informations, consultez [Classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3625 :

```cpp
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
