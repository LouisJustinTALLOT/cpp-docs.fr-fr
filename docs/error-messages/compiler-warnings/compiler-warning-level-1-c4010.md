---
title: Compilateur avertissement (niveau 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 40c6724daf17c1c0b546bb7bc64bb704f732e8d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386549"
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