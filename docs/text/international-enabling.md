---
title: Compatibilité internationale
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: b6c645bafef87ed0b2d43903f4752ef659d79f89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375806"
---
# <a name="international-enabling"></a>Compatibilité internationale

La plupart des codes C et CMD traditionnels font des hypothèses sur la manipulation des caractères et des cordes qui ne fonctionnent pas bien pour les applications internationales. Bien que MFC et la bibliothèque de course-temps de soutien Unicode ou MBCS, il ya encore du travail pour vous de faire. Pour vous guider, cette section explique le sens de « l’activation internationale » dans Visual Cô :

- Unicode et MBCS sont activés au moyen de types de données portables dans les listes de paramètres de fonction MFC et les types de retour. Ces types sont définis sous condition de la manière appropriée, selon que votre build définit le symbole `_UNICODE` ou le symbole `_MBCS` (ce qui signifie DBCS). Différentes variantes des bibliothèques MFC sont automatiquement liées à votre application, selon les deux symboles définis par votre build.

- Le code de bibliothèque de classe utilise des fonctions portables de temps d’exécution et d’autres moyens pour assurer le comportement correct d’Unicode ou de MBCS.

- Vous devez toujours gérer certains types de tâches d’internationalisation dans votre code :

  - Utilisez les mêmes fonctions portables de temps d’exécution qui rendent MFC portable dans l’un ou l’autre environnement.

  - Rendre les cordes littérales et les caractères portables sous l’un ou l’autre environnement, en utilisant la `_T` macro. Pour plus d’informations, voir [Generic-Text Mappings in tchar.h](../text/generic-text-mappings-in-tchar-h.md).

  - Prenez des précautions lors de l’analyse des cordes sous MBCS. Ces précautions ne sont pas nécessaires en vertu d’Unicode. Pour plus d’informations, voir [conseils de programmation MBCS](../text/mbcs-programming-tips.md).

  - Faites attention si vous mélangez des caractères ANSI (8 bits) et Unicode (16 bits) dans votre application. Il est possible d’utiliser des caractères ANSI dans certaines parties de votre programme et des caractères Unicode dans d’autres, mais vous ne pouvez pas les mélanger dans la même chaîne.

  - Ne pas coder dur les chaînes dans votre application. Au lieu de cela, faites-en les ressources STRINGTABLE en les ajoutant au fichier .rc de l’application. Votre application peut alors être localisée sans nécessiter de modifications ou de recomplification du code source. Pour plus d’informations sur les ressources stringTABLE, voir [String Editor](../windows/string-editor.md).

> [!NOTE]
> Les ensembles de personnages européens et MBCS ont quelques personnages, tels que des lettres accentuées, avec des codes de caractère supérieurs à 0x80. Parce que la plupart des codes utilise des caractères signés, ces caractères supérieurs à 0x80 sont proxrogés lorsqu’ils sont convertis **en int**. Il s’agit d’un problème pour l’indexation de tableau parce que les caractères signés, étant négatifs, indexes en dehors du tableau. Les langues qui utilisent MBCS, comme le japonais, sont également uniques. Parce qu’un personnage peut se composer de 1 ou 2 octets, vous devez toujours manipuler les deux octets en même temps.

## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Stratégies d’internationalisation](../text/internationalization-strategies.md)
