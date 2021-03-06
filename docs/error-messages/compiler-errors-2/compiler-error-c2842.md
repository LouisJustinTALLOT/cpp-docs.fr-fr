---
description: 'En savoir plus sur : erreur du compilateur C2842'
title: Erreur du compilateur C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: f086c6c5fcfa451f320d96470615e4f5f4d5674a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119981"
---
# <a name="compiler-error-c2842"></a>Erreur du compilateur C2842

> '*classe*' : un type managé ou WinRT ne peut pas définir son propre’operator new’ou’operator delete'

## <a name="remarks"></a>Notes

Vous pouvez définir votre propre **opérateur New** ou **operator delete** pour gérer l’allocation de mémoire sur le tas natif. Toutefois, les classes de référence ne peuvent pas définir ces opérateurs car ils sont alloués seulement sur le tas managé.

Pour plus d’informations, consultez [opérateurs définis par l’utilisateur (C++/CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2842.

```cpp
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
