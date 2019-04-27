---
title: Opérateurs de collage de jeton (##)
ms.date: 11/04/2016
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: dab4da5fd65fc280d2061256a580a015917d24b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179592"
---
# <a name="token-pasting-operator-"></a>Opérateurs de collage de jeton (##)

L’opérateur double-number-sign ou « collage de jeton » (**##**), qui est parfois appelé l’opérateur « fusion », est utilisé dans les macros object-like et de type fonction. Il permet aux jetons séparés d'être regroupés en un seul jeton et ne peut donc pas être le premier ou dernier jeton de la définition de macro.

Si un paramètre formel d’une définition de macro est précédé ou suivi d’un opérateur de collage de jeton, le paramètre formel est immédiatement remplacé par l’argument réel non étendu. L’expansion de macro n’est pas exécutée sur l’argument avant son remplacement.

Ensuite, chaque occurrence de l’opérateur de collage de jeton dans *chaîne de jeton* est supprimé, et les jetons le précédant ou suivant sont concaténés. Le jeton résultant doit être un jeton valide. Dans ce cas, le jeton est analysé en vue de son remplacement éventuel lorsqu'il représente un nom de macro. L'identificateur représente le nom sous lequel les jetons concaténés sont connus dans le programme avant leur remplacement. Chaque jeton représente un jeton défini ailleurs, soit dans le programme, soit sur la ligne de commande du compilateur. L'espace blanc précédent ou suivant l'opérateur est facultatif.

Cet exemple illustre l'utilisation de l'opérateur stringizing et de l'opérateur de collage de jeton lors de la spécification de la sortie du programme :

```cpp
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;
```

Si une macro est appelée avec un argument numérique comme

```cpp
paster( 9 );
```

la macro génère

```cpp
printf_s( "token" "9" " = %d", token9 );
```

qui devient

```cpp
printf_s( "token9 = %d", token9 );
```

## <a name="example"></a>Exemple

```cpp
// preprocessor_token_pasting.cpp
#include <stdio.h>
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;

int main()
{
   paster(9);
}
```

```Output
token9 = 9
```

## <a name="see-also"></a>Voir aussi

[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)