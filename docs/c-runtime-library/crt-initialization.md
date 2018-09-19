---
title: Initialisation du CRT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 965955cf5c92ba627227292d513c9b2bda57cd48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031918"
---
# <a name="crt-initialization"></a>Initialisation du CRT

Cette rubrique décrit comment la bibliothèque CRT initialise les états globaux dans le code natif.

Par défaut, l’éditeur de liens inclut la bibliothèque CRT, qui fournit son propre code de démarrage. Ce code de démarrage initialise la bibliothèque CRT, appelle les initialiseurs globaux, puis appelle la fonction `main` fournie par l’utilisateur pour les applications console.

## <a name="initializing-a-global-object"></a>Initialisation d’un objet global

Examinons le code ci-dessous.

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

Selon la norme C/C++, `func()` doit être appelé avant l’exécution de `main()`. Mais qui l’appelle ?

Une façon de déterminer cela consiste à définir un point d’arrêt dans `func()`, de déboguer l’application et d’examiner la pile. Cela est possible, car le code source de la bibliothèque CRT est inclus avec Visual Studio.

Lorsque vous parcourez les fonctions sur la pile, vous constaterez que la bibliothèque CRT effectue une boucle dans une liste de pointeurs de fonction et appelle chacun de ces fonctions lorsqu’il les rencontre. Ces fonctions sont similaires à `func()` ou aux constructeurs pour les instances de classe.

La bibliothèque CRT obtient la liste des pointeurs de fonction du compilateur Visual C++. Lorsque le compilateur détecte un initialiseur global, il génère un initialiseur dynamique dans la section `.CRT$XCU` (où `CRT` est le nom de section et `XCU` est le nom du groupe). Pour obtenir une liste de ces initialiseurs dynamiques, exécutez la commande **dumpbin /all main.obj**, puis recherchez la section `.CRT$XCU` (lorsque main.cpp est compilé dans un fichier C++, et non un fichier C). Il sera semblable à ce qui suit :

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                                Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  ------
00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

La bibliothèque CRT définit deux pointeurs :

- `__xc_a` dans `.CRT$XCA`

- `__xc_z` dans `.CRT$XCZ`

Les deux groupes n’ont pas d’autres symboles définis à l’exception de `__xc_a` et `__xc_z`.

Maintenant, lorsque l’éditeur de liens lit différents groupes `.CRT`, il les regroupe dans une section et les trie par ordre alphabétique. Cela signifie que les initialiseurs globaux définis par l’utilisateur (que le compilateur Visual C++ place dans `.CRT$XCU`) viendront toujours après `.CRT$XCA` et avant `.CRT$XCZ`.

La section ressemble à ce qui suit :

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

Par conséquent, la bibliothèque CRT utilise à la fois `__xc_a` et `__xc_z` pour déterminer le début et la fin de la liste d’initialiseurs globaux en raison de la façon de laquelle ils sont disposés en mémoire une fois que l’image est chargée.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)