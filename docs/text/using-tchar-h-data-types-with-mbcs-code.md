---
title: Utilisation de types de données TCHAR.H avec _MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 78e5d89e1e87d081e762fab1298eb990b914324c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446595"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>Utilisation de types de données TCHAR.H avec _MBCS

Lorsque la constante de manifeste `_MBCS` est définie, une routine de texte générique donnée correspond à l’un des types de routines suivants :

- Une routine SBCS qui gère correctement les chaînes, caractères et caractères multioctets. Dans ce cas, les arguments de chaîne doivent être de type `char*`. Par exemple, `_tprintf` est mappé sur `printf` ; les arguments de chaîne dans `printf` sont de type `char*`. Si vous utilisez le type de données de texte générique `_TCHAR` pour vos types de chaîne, les types de paramètre formels et réels pour `printf` correspondent car `_TCHAR*` est mappé sur `char*`.

- Une routine spécifique à MBCS. Dans ce cas, les arguments de chaîne doivent être de type `unsigned char*`. Par exemple, `_tcsrev` est mappé sur `_mbsrev`, qui attend et retourne une chaîne de type `unsigned char*`. Si vous utilisez le `_TCHAR` type de données de texte générique pour vos types de chaîne, il y a un conflit de type potentiel, car `_TCHAR` est mappé au type `char`.

Voici les trois solutions pour empêcher ce conflit de types (et les avertissements du compilateur C ou erreurs du compilateur C++ qui en découleraient) :

- Utiliser le comportement par défaut. Tchar. h fournit des prototypes de routine de texte générique pour les routines dans les bibliothèques Runtime, comme dans l’exemple suivant.

    ```cpp
    char * _tcsrev(char *);
    ```

   Dans le cas par défaut, le prototype de `_tcsrev` est mappé à `_mbsrev` via un thunk dans libc. lib. Cela modifie les types du `_mbsrev` paramètres entrants et la valeur de retour sortante à partir de `_TCHAR*` (autrement dit, `char *`) en `unsigned char *`. Cette méthode garantit la correspondance de type lorsque vous utilisez `_TCHAR`, mais elle est relativement lente en raison de la surcharge de l’appel de fonction.

- Utilisez la fonction inline en incorporant l’instruction du préprocesseur suivante dans votre code.

    ```cpp
    #define _USE_INLINING
    ```

   Cette méthode provoque un thunk de fonction inline, fourni dans Tchar. h, pour mapper la routine de texte générique directement à la routine MBCS appropriée. L’extrait de code suivant de Tchar. h fournit un exemple de cette opération.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   Si vous pouvez utiliser l’incorporation, il s’agit de la meilleure solution, car elle garantit une correspondance de types et ne présente aucun coût supplémentaire en termes de temps.

- Utilisez le mappage direct en incorporant l’instruction de préprocesseur suivante dans votre code.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   Cette approche constitue une alternative rapide si vous ne souhaitez pas utiliser le comportement par défaut ou que vous ne pouvez pas utiliser l’incorporation. La routine de texte générique est alors mappée par une macro directement à la version MBCS de la routine, comme dans l’exemple suivant de Tchar. h.

    ```cpp
    #define _tcschr _mbschr
    ```

   Lorsque vous adoptez cette approche, vous devez veiller à utiliser les types de données appropriés pour les arguments de chaîne et les valeurs de retour de chaîne. Vous pouvez utiliser la conversion de type pour assurer la bonne correspondance des types, ou vous pouvez utiliser le type de données de texte générique `_TXCHAR`. `_TXCHAR` est mappée au type **char** dans du code SBCS mais est mappée au type **unsigned char** dans le code MBCS. Pour plus d’informations sur les macros de texte générique, consultez [mappages de texte générique](../c-runtime-library/generic-text-mappings.md) dans la référence de la *bibliothèque Runtime*.

## <a name="see-also"></a>Voir aussi

[Mappages de texte générique dans tchar.h](../text/generic-text-mappings-in-tchar-h.md)
