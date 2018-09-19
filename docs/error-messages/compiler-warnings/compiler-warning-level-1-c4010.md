---
title: Compilateur avertissement (niveau 1) C4010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52449689d329cee45cc69b63c315ce9335befbe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073096"
---
# <a name="compiler-warning-level-1-c4010"></a>Compilateur avertissement (niveau 1) C4010

commentaire sur une ligne contient le caractère de continuation de ligne

Un commentaire sur une ligne, qui est introduit par / /, contient une barre oblique inverse (\\) qui sert d’un caractère de continuation de ligne. Le compilateur considère que la ligne suivante est une suite et la traite comme un commentaire.

Certains syntaxiques éditeurs n’indiquent pas la ligne qui suit le caractère de continuation en tant que commentaire. Ignorer les couleurs de syntaxe sur toutes les lignes qui provoquent cet avertissement.

L’exemple suivant génère l’erreur C4010 :

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```