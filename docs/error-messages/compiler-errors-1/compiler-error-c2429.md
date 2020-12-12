---
description: 'En savoir plus sur : erreur du compilateur C2429'
title: Erreur du compilateur C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: 3c16a2a430e8050103c3903cf1355de089252ed5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190131"
---
# <a name="compiler-error-c2429"></a>Erreur du compilateur C2429

> '*Language Feature*'requiert l’indicateur de compilateur'*option du compilateur*'

La fonctionnalité de langage nécessite une option de compilateur spécifique pour la prise en charge.

L’erreur **C2429 : la fonctionnalité de langage’Nested-namespace-Definition’requiert l’indicateur de compilateur'/std : c++ 17 '** est généré si vous essayez de définir un espace de noms *composé*, un espace de noms qui contient un ou plusieurs noms d’espaces de noms imbriqués dans l’étendue, à partir de Visual Studio 2015 Update 5. (Dans Visual Studio 2017 version 15,3, le commutateur **/std : c + + latest** est requis.) Les définitions d’espaces de noms composés ne sont pas autorisées en C++ avant C++ 17. Le compilateur prend en charge les définitions d’espaces de noms composés lorsque l’option de compilateur [/std : c++ 17](../../build/reference/std-specify-language-standard-version.md) est spécifiée :

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual Studio 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
