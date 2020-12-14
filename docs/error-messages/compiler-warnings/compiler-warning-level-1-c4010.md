---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4010'
title: Avertissement du compilateur (niveau 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 899e34e0835cce02ab5d11b6c64ae604369f93d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241584"
---
# <a name="compiler-warning-level-1-c4010"></a>Avertissement du compilateur (niveau 1) C4010

un commentaire sur une seule ligne contient un caractère de continuation de ligne

Un commentaire sur une seule ligne, qui est introduit par//, contient une barre oblique inverse ( \\ ) qui sert de caractère de continuation de ligne. Le compilateur considère que la ligne suivante est une continuation et la traite comme un commentaire.

Certains éditeurs orientés syntaxe n’indiquent pas la ligne qui suit le caractère de continuation en tant que commentaire. Ignore la coloration de la syntaxe sur les lignes qui provoquent cet avertissement.

L’exemple suivant génère l’C4010 :

```cpp
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```
