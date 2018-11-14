---
title: Erreur du compilateur C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: 99b2c86d1e914c9425c2664d4e858bba6cb99486
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325558"
---
# <a name="compiler-error-c2842"></a>Erreur du compilateur C2842

> «*classe*' : managé ou WinRT type ne peut pas définir son propre 'operator new' ou 'operator delete'

## <a name="remarks"></a>Notes

Vous pouvez définir vos propres **opérateur new** ou **opérateur delete** pour gérer l’allocation de mémoire sur le tas natif. Toutefois, les classes de référence ne peuvent pas définir ces opérateurs car ils sont alloués seulement sur le tas managé.

Pour plus d’informations, consultez [les opérateurs définis par l’utilisateur (C++ / c++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2842.

```cpp
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
