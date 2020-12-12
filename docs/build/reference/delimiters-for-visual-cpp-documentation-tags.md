---
description: 'En savoir plus sur les éléments suivants : délimiteurs pour les balises de documentation Visual C++'
title: Délimiteurs pour les étiquettes de documentation Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
ms.openlocfilehash: 7878fa0454af9eb09c4aa537a3e59d8af4a3ee87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201467"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Délimiteurs pour les étiquettes de documentation Visual C++

L’utilisation de balises de documentation exige des délimiteurs, qui indiquent au compilateur où un commentaire de documentation commence et se termine.

Vous pouvez utiliser les genres de délimiteurs ci-dessous avec les balises de documentation XML :

| Délimiteur | Description |
|-|-|
| `///` | Il s’agit de la forme qui est présentée dans les exemples de documentation et utilisée par les modèles de projet Visual Studio C++.  |
| `/** */`  | Ce sont des délimiteurs multilignes.  |

Des règles de mise en forme s’appliquent quand vous utilisez les délimiteurs `/** */` :

- Pour la ligne qui contient le délimiteur `/**`, si le reste de la ligne est un espace blanc, la ligne n’est pas traitée dans le cadre des commentaires. Si le premier caractère est un espace blanc, ce caractère est ignoré et le reste de la ligne est traité. Sinon, tout le texte de la ligne après le délimiteur `/**` est traité comme faisant partie du commentaire.

- Pour la ligne qui contient le délimiteur `*/`, s’il n’y a que des espaces blancs jusqu’au délimiteur `*/`, cette ligne est ignorée. Sinon, le texte de la ligne jusqu’au délimiteur `*/` est traité comme faisant partie du commentaire, conformément aux règles de critères spéciaux décrites dans la puce suivante.

- Pour les lignes qui suivent celle qui commence par le délimiteur `/**`, le compilateur recherche un modèle commun au début de chaque ligne qui consiste en un espace blanc facultatif et un astérisque (`*`) suivi d’autres espaces blancs facultatifs. Si le compilateur trouve un ensemble commun de caractères au début de chaque ligne, il ignore ce modèle pour toutes les lignes qui suivent le délimiteur `/**`, jusqu’à la ligne (en l’incluant éventuellement) qui contient le délimiteur `*/`.

Exemples :

- La seule partie du commentaire suivant qui sera traitée est la ligne qui commence par `<summary>`. Les deux formats de balise suivants produisent les mêmes commentaires :

    ```cpp
    /**
    <summary>text</summary>
    */
    /** <summary>text</summary> */
    ```

- Le compilateur applique un modèle « \* » à ignorer au début des deuxième et troisième lignes.

    ```cpp
    /**
     * <summary>
     *  text </summary>*/
    ```

- Le compilateur ne trouve aucun modèle dans ce commentaire, car la deuxième ligne n’a pas d’astérisque. Ainsi, tout le texte des deuxième et troisième lignes est traité comme faisant partie du commentaire jusqu’au délimiteur `*/`.

    ```cpp
    /**
     * <summary>
       text </summary>*/
    ```

- Le compilateur ne trouve pas de modèle dans ce commentaire pour deux raisons. Tout d’abord, aucune ligne ne commence par un nombre constant d’espaces avant l’astérisque. Ensuite, la cinquième ligne commence par une tabulation, qui ne correspond pas à des espaces. Ainsi, tout le texte de la deuxième ligne jusqu’à `*/` est traité comme faisant partie du commentaire.

    ```cpp
    /**
      * <summary>
      * text
     *  text2
       *  </summary>
    */
    ```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
