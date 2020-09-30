---
title: Erreur du compilateur C3381
description: Erreur du compilateur Microsoft C++ C3381, ses causes et comment les résoudre.
ms.date: 09/28/2020
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: 48a6c81f9506c532333b5353b8b194d17c91043f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510152"
---
# <a name="compiler-error-c3381"></a>Erreur du compilateur C3381

> '*identificateur*' : les spécificateurs d’accès à l’assembly ne sont disponibles que dans le code compilé avec une option/clr

Un type a été déclaré ou défini à l’aide d’un spécificateur d’accès, qui est autorisé uniquement dans le code compilé à l’aide de **`/clr`** .

## <a name="remarks"></a>Remarques

Cette erreur peut être due à un mot clé introuvable **`public`** , **`protected`** , ou **`private`** , ou à un signe deux-points ( **`:`** ) manquant après un spécificateur d’accès dans un **`class`** ou un **`struct`** .

En C++/CLI, les types natifs peuvent être visibles à l’extérieur d’un assembly, mais vous pouvez uniquement spécifier l’accès à l’assembly pour les types natifs dans une **`/clr`** compilation. Pour plus d’informations, consultez la rubrique [visibilité des types](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) et [ `/clr` (compilation du Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3381. Pour corriger ce problème, supprimez d’abord le **`public`** spécificateur de la `class A` définition, ou compilez à l’aide de l' **`/clr`** option. Ensuite, ajoutez un signe deux-points après **`private`** pour spécifier l’accès pour `class B {} b;` . Cela est dû au fait qu’une classe imbriquée ne peut pas avoir de spécificateur d’accès à l’assembly dans le cadre de sa déclaration.

```cpp
// C3381.cpp
// compile with: /c
public class A {   // C3381
    private class B {} b;   // C3381
};
```
