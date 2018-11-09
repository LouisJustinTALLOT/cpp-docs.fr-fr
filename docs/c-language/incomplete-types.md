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
ms.openlocfilehash: 9f0df4c28fc0da860d5a903b3f2833a328312dd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433499"
---
# <a name="incomplete-types"></a>Types incomplets

Un *type incomplet* est un type qui décrit un identificateur, mais qui ne présente pas les informations nécessaires pour permettre d'en déterminer la taille. Un type incomplet peut être :

- un type de structure dont vous n'avez pas encore spécifié les membres ;

- un type d'union dont vous n'avez pas encore spécifié les membres ;

- un type de tableau dont vous n'avez pas encore spécifié la dimension.

Le type **void** est un type incomplet qui ne peut pas être complété. Pour compléter un type incomplet, spécifiez les informations manquantes. Les exemples ci-dessous montrent comment créer et compléter des types incomplets.

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

- Pour créer un type de tableau incomplet, déclarez un type de tableau sans spécifier son nombre de répétitions. Exemple :

    ```C
    char a[];  /* a has incomplete type */
    ```

- Pour compléter un type de tableau incomplet, déclarez le même nom ultérieurement dans la même portée en spécifiant son nombre de répétitions, comme suit :

    ```C
    char a[25]; /* a now has complete type */
    ```

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)