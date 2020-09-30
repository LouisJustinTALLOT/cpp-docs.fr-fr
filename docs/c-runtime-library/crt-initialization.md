---
title: Initialisation du CRT
description: Décrit comment le CRT Initialise l’état global dans le code natif.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: 25f1e2a7e5b7d91c729bb45bd79ba9a8720cead1
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589768"
---
# <a name="crt-initialization"></a>Initialisation du CRT

Cette rubrique décrit comment le CRT Initialise l’état global dans le code natif.

Par défaut, l’éditeur de liens inclut la bibliothèque CRT, qui fournit son propre code de démarrage. Ce code de démarrage initialise la bibliothèque CRT, appelle les initialiseurs globaux, puis appelle la fonction `main` fournie par l’utilisateur pour les applications console.

## <a name="initializing-a-global-object"></a>Initialisation d’un objet global

Considérez le code suivant :

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

Une façon de déterminer l’appelant consiste à définir un point d’arrêt dans `func()` , à déboguer l’application et à examiner la pile. Cela est possible, car le code source de la bibliothèque CRT est inclus avec Visual Studio.

Lorsque vous parcourez les fonctions sur la pile, vous verrez que le CRT appelle une liste de pointeurs de fonction. Ces fonctions sont similaires aux `func()` constructeurs ou aux instances de classe.

La bibliothèque CRT obtient la liste des pointeurs de fonction du compilateur Microsoft C++. Quand le compilateur voit un initialiseur global, il génère un initialiseur dynamique dans la `.CRT$XCU` section où `CRT` est le nom de la section et `XCU` est le nom du groupe. Pour obtenir une liste d’initialiseurs dynamiques, exécutez la commande **DUMPBIN/all main. obj**, puis recherchez la `.CRT$XCU` section. Cela s’applique lorsque main. cpp est compilé en tant que fichier C++, et non en tant que fichier C. Elle est similaire à l’exemple suivant :

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
--------  ----------------  -----------------  --------  -------
00000000  DIR32             00000000           C         ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

La bibliothèque CRT définit deux pointeurs :

- `__xc_a` dans `.CRT$XCA`

- `__xc_z` dans `.CRT$XCZ`

Aucun groupe n’a d’autres symboles définis à l’exception `__xc_a` de et `__xc_z` .

Maintenant, lorsque l’éditeur de liens lit différents groupes `.CRT`, il les regroupe dans une section et les trie par ordre alphabétique. Cela signifie que les initialiseurs globaux définis par l’utilisateur (que le compilateur Microsoft C++ place dans `.CRT$XCU`) viendront toujours après `.CRT$XCA` et avant `.CRT$XCZ`.

La section doit ressembler à l’exemple suivant :

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

Par conséquent, la bibliothèque CRT utilise `__xc_a` à la fois et `__xc_z` pour déterminer le début et la fin de la liste des initialiseurs globaux en raison de la façon dont ils sont disposés en mémoire après le chargement de l’image.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
