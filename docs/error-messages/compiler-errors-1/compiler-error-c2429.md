---
title: C2429 d’erreur du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/16/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2429
dev_langs:
- C++
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 032df433b28e83f720fe76952a541b59bda889f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227814"
---
# <a name="compiler-error-c2429"></a>C2429 d’erreur du compilateur

> '*fonctionnalité de langage*'requiert l’indicateur de compilateur'*option du compilateur*'

La fonctionnalité de langage requiert une option du compilateur spécifique pour la prise en charge.

L’erreur **C2429 : fonctionnalité de langage 'nested-namespace-definition' nécessite l’indicateur de compilateur ' / std:c ++ 17** est générée si vous essayez de définir un *espace de noms composé*, un espace de noms qui contient un ou plusieurs noms d’espace de noms imbriqué à l’étendue, à partir de Visual Studio 2015 Update 5. (Dans Visual Studio 2017 version 15.3, le **/std : c ++ dernière** commutateur est requis.) Compound, espace de noms définitions ne sont pas autorisées en C++ avant C ++ 17. Le compilateur prend en charge les définitions de l’espace de noms composé lorsque le [/std : c ++ 17](../../build/reference/std-specify-language-standard-version.md) option du compilateur est spécifiée :

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
