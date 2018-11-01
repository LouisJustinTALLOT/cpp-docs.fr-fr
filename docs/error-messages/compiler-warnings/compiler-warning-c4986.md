---
title: Avertissement du compilateur C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: fb52e33ceeadda03105e391d8e0b5b3f6234d6b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499123"
---
# <a name="compiler-warning-c4986"></a>Avertissement du compilateur C4986

'fonction' : spécification d’exception ne correspond pas à la déclaration précédente

Cet avertissement peut être généré lorsqu’il existe une spécification d’exception dans une déclaration et pas dans l’autre.

Par défaut, C4986 est désactivé. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4986.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

## <a name="example"></a>Exemple

L’exemple suivant permet d’éliminer cet avertissement.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1() throw (X*)
{
    // ...
}
```