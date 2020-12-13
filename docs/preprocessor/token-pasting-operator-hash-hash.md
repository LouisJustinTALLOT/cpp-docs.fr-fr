---
description: 'En savoir plus sur : opérateur de collage de jeton (# #)'
title: Opérateur de collage de jeton (##)
ms.date: 08/29/2019
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: 3bad0a615fdf7c0b3e1e54d16c25e37bf495072c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149667"
---
# <a name="token-pasting-operator-"></a>Opérateur de collage de jeton (##)

Le signe double-dièse ou l’opérateur de *collage de jeton* ( **##** ), qui est parfois appelé opérateur de *fusion* ou de *combinaison* , est utilisé à la fois dans les macros de type objet et de type fonction. Il permet de joindre des jetons distincts à un jeton unique et, par conséquent, ne peut pas être le premier ou le dernier jeton dans la définition de macro.

Si un paramètre formel d’une définition de macro est précédé ou suivi d’un opérateur de collage de jeton, le paramètre formel est immédiatement remplacé par l’argument réel non étendu. L’expansion de macro n’est pas exécutée sur l’argument avant son remplacement.

Ensuite, chaque occurrence de l’opérateur de collage de jeton dans *Token-String* est supprimée, et les jetons qui le précèdent et le suivent sont concaténés. Le jeton résultant doit être un jeton valide. Dans ce cas, le jeton est analysé en vue de son remplacement éventuel lorsqu'il représente un nom de macro. L'identificateur représente le nom sous lequel les jetons concaténés sont connus dans le programme avant leur remplacement. Chaque jeton représente un jeton défini ailleurs, soit dans le programme, soit sur la ligne de commande du compilateur. L'espace blanc précédent ou suivant l'opérateur est facultatif.

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
