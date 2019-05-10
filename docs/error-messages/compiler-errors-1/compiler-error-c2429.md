---
title: Erreur du compilateur C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: a5d1e98e91c541729a93f731eede9b047589c63a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447985"
---
# <a name="compiler-error-c2429"></a>Erreur du compilateur C2429

> «*fonctionnalité de langage*'nécessite l’indicateur de compilateur'*option du compilateur*»

La fonctionnalité de langage nécessite une option de compilateur spécifique de prise en charge.

L’erreur **C2429 : fonctionnalité de langage 'nested-namespace-definition' nécessite l’indicateur de compilateur ' / std : c ++ 17'** est générée si vous tentez de définir un *espace de noms composé*, un espace de noms qui contient un ou plusieurs étendue imbriquée de noms, à compter de Visual Studio 2015 Update 5. (Dans Visual Studio 2017 version 15.3, le **/std : c ++ dernière** commutateur est requis.) Composée d’espace de noms définitions ne sont pas autorisées en C++ avant C ++ 17. Le compilateur prend en charge les définitions d’espace de noms composés lorsque le [/std : c ++ 17](../../build/reference/std-specify-language-standard-version.md) option du compilateur est spécifiée :

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual Studio 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
