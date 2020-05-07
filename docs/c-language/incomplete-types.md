---
title: Types incomplets
ms.date: 11/04/2016
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
ms.openlocfilehash: e7a5cd7624b55e7bce0fbd09451ab42426f5bc37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232890"
---
# <a name="incomplete-types"></a>Types incomplets

Un *type incomplet* est un type qui décrit un identificateur, mais qui ne contient pas les informations nécessaires pour déterminer la taille de l’identificateur. Un type incomplet peut être :

- un type de structure dont vous n'avez pas encore spécifié les membres ;

- un type d'union dont vous n'avez pas encore spécifié les membres ;

- un type de tableau dont vous n'avez pas encore spécifié la dimension.

Le type **void** est un type incomplet qui ne peut pas être terminé. Pour compléter un type incomplet, spécifiez les informations manquantes. Les exemples ci-dessous montrent comment créer et compléter des types incomplets.

- Pour créer un type de structure incomplet, déclarez un type de structure sans spécifier ses membres. Dans l'exemple ci-dessous, le pointeur `ps` pointe vers un type de structure incomplet nommé `student`.

    ```C
    struct student *ps;
    ```

- Pour compléter un type de structure incomplet, déclarez le même type de structure ultérieurement dans la même portée en spécifiant ses membres, comme suit :

    ```C
    struct student
    {
        int num;
    }                   /* student structure now completed */
    ```

- Pour créer un type de tableau incomplet, déclarez un type de tableau sans spécifier son nombre de répétitions. Par exemple :

    ```C
    char a[];  /* a has incomplete type */
    ```

- Pour compléter un type de tableau incomplet, déclarez le même nom ultérieurement dans la même portée en spécifiant son nombre de répétitions, comme suit :

    ```C
    char a[25]; /* a now has complete type */
    ```

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)
