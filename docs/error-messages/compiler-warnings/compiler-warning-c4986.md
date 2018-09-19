---
title: Avertissement du compilateur C4986 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4986
dev_langs:
- C++
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f464f2a6e1f76c7d8b9de8bcc2353766aff0854
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077059"
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