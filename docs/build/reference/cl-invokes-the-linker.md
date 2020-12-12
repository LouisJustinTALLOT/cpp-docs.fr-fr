---
description: 'En savoir plus sur : CL appelle l’éditeur de liens'
title: CL appelle l'éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: ddd693cdba625756b8085d2f8cb3870d8cdc6add
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179159"
---
# <a name="cl-invokes-the-linker"></a>CL appelle l'éditeur de liens

CL appelle automatiquement l’éditeur de liens après la compilation, sauf si l’option/c est utilisée. CL transmet à l’éditeur de liens les noms des fichiers. obj créés lors de la compilation et les noms de tous les autres fichiers spécifiés sur la ligne de commande. L’éditeur de liens utilise les options listées dans la variable d’environnement LINK. Vous pouvez utiliser l’option/Link pour spécifier les options de l’éditeur de liens sur la ligne de commande CL. Les options qui suivent l’option/Link remplacent celles de la variable d’environnement LINK. Les options du tableau suivant suppriment la liaison.

|Option|Description|
|------------|-----------------|
|/C|Compiler sans liaison|
|/E,/EP,/P|Prétraiter sans compilation ou liaison|
|/Zg|Générer des prototypes de fonction|
|/Zs|Vérifier la syntaxe|

Pour plus d’informations sur la liaison, consultez Options de l' [éditeur de liens MSVC](linker-options.md).

## <a name="example"></a>Exemple

Supposons que vous compilez trois fichiers sources C : MAIN. c, MOD1. c et MOD2. c. Chaque fichier comprend un appel à une fonction définie dans un autre fichier :

- MAIN. c appelle la fonction `func1` dans MOD1. c et la fonction `func2` dans Mod2. c.

- MOD1. c appelle les fonctions de bibliothèque standard `printf_s` et `scanf_s` .

- MOD2. c appelle les fonctions graphiques nommées `myline` et `mycircle` , qui sont définies dans une bibliothèque nommée MYGRAPH. lib.

Pour générer ce programme, compilez avec la ligne de commande suivante :

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL compile d’abord les fichiers sources C et crée les fichiers objets MAIN. obj, MOD1. objet MOD2. obj. Le compilateur place le nom de la bibliothèque standard dans chaque fichier. obj. Pour plus d’informations, consultez [utiliser la bibliothèque de Run-Time](md-mt-ld-use-run-time-library.md).

CL passe les noms des fichiers. obj, ainsi que le nom MYGRAPH. lib, à l’éditeur de liens. L’éditeur de liens résout les références externes comme suit :

1. Dans MAIN. obj, la référence à `func1` est résolue à l’aide de la définition dans MOD1. obj ; la référence à `func2` est résolue à l’aide de la définition dans Mod2. obj.

1. Dans MOD1. obj, les références à `printf_s` et à `scanf_s` sont résolues à l’aide des définitions de la bibliothèque que l’éditeur de liens trouve nommé dans MOD1. obj.

1. Dans MOD2. obj, les références à `myline` et à `mycircle` sont résolues à l’aide des définitions dans MYGRAPH. lib.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Définition des options du compilateur](compiler-command-line-syntax.md)
