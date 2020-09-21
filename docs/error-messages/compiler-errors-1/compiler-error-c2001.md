---
title: Erreur du compilateur C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 6b40a3bd186b5c45a0ea5163f433635ab1e7b07f
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743488"
---
# <a name="compiler-error-c2001"></a>Erreur du compilateur C2001

saut de ligne dans la constante

Une constante de chaîne ne peut pas être poursuivie sur une deuxième ligne, sauf si vous procédez comme suit :

- Terminez la première ligne par une barre oblique inverse.

- Fermez la chaîne sur la première ligne avec un guillemet double et ouvrez la chaîne sur la ligne suivante avec un autre guillemet double.

La fin de la première ligne avec \n n’est pas suffisante.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2001 :

```cpp
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

Les espaces au début de la ligne suivante après un caractère de continuation de ligne sont inclus dans la constante de chaîne. Aucun des exemples ci-dessus n’incorpore un caractère de saut de ligne dans la constante de chaîne. Vous pouvez incorporer un caractère de saut de ligne comme indiqué ici :

```cpp
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
