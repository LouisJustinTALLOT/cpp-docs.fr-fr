---
description: 'En savoir plus sur : avertissement du compilateur C4986'
title: Avertissement du compilateur C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: 5d068ee376c6ae6ce1fb3563d66c7bda871da0ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336038"
---
# <a name="compiler-warning-c4986"></a>Avertissement du compilateur C4986

'fonction' : la spécification d’exception ne correspond pas à la déclaration précédente

Cet avertissement peut être généré lorsqu’il existe une spécification d’exception dans une déclaration et non dans l’autre.

Par défaut, C4986 est désactivé. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C4986.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

L’exemple suivant élimine cet avertissement.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1() throw (X*)
{
    // ...
}
```
