---
title: Erreur du compilateur C2001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71048a706678e4d9e6906972ebf148748927e829
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088240"
---
# <a name="compiler-error-c2001"></a>Erreur du compilateur C2001

saut de ligne dans la constante

Constante de chaîne ne peut pas se poursuivre sur une deuxième ligne, sauf si vous procédez comme suit :

- La première ligne avec une barre oblique inverse de fin.

- Fermez la chaîne sur la première ligne avec un guillemet double et ouvrez la chaîne sur la ligne suivante avec un autre guillemet double.

Fin de la première ligne \n n’est pas suffisant.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2001 :

```
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

## <a name="example"></a>Exemple

Les espaces au début de la ligne suivante après un caractère de continuation de ligne sont inclus dans la constante de chaîne. Aucun des exemples ci-dessus incorporer un caractère de saut de ligne dans la constante de chaîne. Vous pouvez incorporer un caractère de saut de ligne comme indiqué ici :

```
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```