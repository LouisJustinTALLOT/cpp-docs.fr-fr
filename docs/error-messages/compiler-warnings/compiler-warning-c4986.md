---
title: Avertissement du compilateur C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: df6fc88ffe98dd2b4a3129800c7881f26d4f625b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164818"
---
# <a name="compiler-warning-c4986"></a>Avertissement du compilateur C4986

'fonction' : la spécification d’exception ne correspond pas à la déclaration précédente

Cet avertissement peut être généré lorsqu’il existe une spécification d’exception dans une déclaration et non dans l’autre.

Par défaut, C4986 est désactivé. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

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
