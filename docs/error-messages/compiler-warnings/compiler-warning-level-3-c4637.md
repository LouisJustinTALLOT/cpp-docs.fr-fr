---
title: Compilateur avertissement (niveau 3) C4637 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4637
dev_langs:
- C++
helpviewer_keywords:
- C4637
ms.assetid: 5fd347c1-2de9-408f-9136-1bf1ff273622
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 094182dd0e438a89ce3652130b411ab1ca1a0bd1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111782"
---
# <a name="compiler-warning-level-3-c4637"></a>Avertissement du compilateur (niveau 3) C4637

Cible de commentaire de document XML : \<inclure > balise ignorée.  raison

La syntaxe d’un [ \<inclure >](../../ide/include-visual-cpp.md) balise n’était pas correcte.

L’exemple suivant génère l’avertissement C4637 :

```
// C4637.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <include file="c:\davedata\jtest\xml_include.doc"/>
   // Try the following line instead:
   // /// <include file='xml_include.doc' path='MyDocs/MyMembers/*' />
   void MyMethod() {
   }
};   // C4637
```