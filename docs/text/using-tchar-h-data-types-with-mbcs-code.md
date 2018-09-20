---
title: À l’aide de TCHAR. Types de données H avec _MBCS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
- TCHAR
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a52dded31c1037130a9e4ee6182003f522c062d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372053"
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>Utilisation de types de données TCHAR.H avec _MBCS

Lorsque la constante de manifeste `_MBCS` est définie, une routine de texte générique donnée correspond à un des types suivants de routines :

- Une routine SBCS qui gère correctement les chaînes, caractères et caractères multioctets. Dans ce cas, les arguments de chaîne doivent être de type `char*`. Par exemple, `_tprintf` est mappé sur `printf` ; les arguments de chaîne dans `printf` sont de type `char*`. Si vous utilisez le type de données de texte générique `_TCHAR` pour vos types de chaîne, les types de paramètre formels et réels pour `printf` correspondent car `_TCHAR*` est mappé sur `char*`.

- Une routine spécifique à MBCS. Dans ce cas, les arguments de chaîne doivent être de type `unsigned char*`. Par exemple, `_tcsrev` est mappé sur `_mbsrev`, qui attend et retourne une chaîne de type `unsigned char*`. Si vous utilisez le `_TCHAR` type de données de texte générique pour vos types de chaîne, il tient un conflit de type `_TCHAR` correspond au type `char`.

Voici les trois solutions pour empêcher ce conflit de types (et les avertissements du compilateur C ou erreurs du compilateur C++ qui en découleraient) :

- Utiliser le comportement par défaut. Tchar.h fournit des prototypes de routine de texte générique pour les routines dans les bibliothèques Runtime, comme dans l’exemple suivant.

    ```cpp
    char * _tcsrev(char *);
    ```

   Dans le cas par défaut, le prototype pour `_tcsrev` est mappé à `_mbsrev` via un thunk dans Libc.lib. Cela transforme les types de la `_mbsrev` paramètres entrants et retournent la valeur de `_TCHAR*` (autrement dit, `char *`) à `unsigned char *`. Cette méthode garantit la correspondance de types lorsque vous utilisez `_TCHAR`, mais elle est relativement lente en raison de la surcharge d’appels de fonction.

- Utilisez la fonction inline en incorporant l’instruction du préprocesseur suivante dans votre code.

    ```cpp
    #define _USE_INLINING
    ```

   Cette méthode provoque un thunk de fonction inline, par Tchar.h, mappe la routine de texte générique directement à la routine MBCS appropriée. L’extrait de code suivant de Tchar.h fournit un exemple de cette procédure.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   Si vous pouvez utiliser l’incorporation, il s’agit de la meilleure solution, car elle garantit une correspondance de types et ne présente aucun coût supplémentaire en termes de temps.

- Utilisez le mappage direct en incorporant l’instruction du préprocesseur suivante dans votre code.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   Cette approche constitue une alternative rapide si vous ne souhaitez pas utiliser le comportement par défaut ou que vous ne pouvez pas utiliser l’incorporation. Elle entraîne la routine de texte générique à être mappée par une macro directement à la version MBCS de la routine, comme dans l’exemple suivant de Tchar.h.

    ```cpp
    #define _tcschr _mbschr
    ```

   Lorsque vous adoptez cette approche, vous devez être attentif garantir une utilisation de types de données appropriés pour les arguments de chaîne et les valeurs de retour de chaîne. Vous pouvez utiliser la conversion de type pour assurer la bonne correspondance des types, ou vous pouvez utiliser le type de données de texte générique `_TXCHAR`. `_TXCHAR` correspond au type **char** dans le code SBCS mais correspond au type **unsigned char** dans le code MBCS. Pour plus d’informations sur les macros de texte générique, consultez [mappages de texte générique](../c-runtime-library/generic-text-mappings.md) dans le *Run-Time Library Reference*.

## <a name="see-also"></a>Voir aussi

[Mappages de texte générique dans Tchar.h](../text/generic-text-mappings-in-tchar-h.md)