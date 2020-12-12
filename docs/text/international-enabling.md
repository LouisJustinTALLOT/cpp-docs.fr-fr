---
description: 'En savoir plus sur : activation internationale'
title: Compatibilité internationale
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: 15db7e27b65f4225917945820c936e572fc5da94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207265"
---
# <a name="international-enabling"></a>Compatibilité internationale

La plupart du code C et C++ traditionnel fait des hypothèses sur les manipulations de caractères et de chaînes qui ne fonctionnent pas correctement pour les applications internationales. Alors que MFC et la bibliothèque Runtime prennent en charge Unicode ou MBCS, vous pouvez continuer à travailler. Pour vous guider, cette section explique la signification de la « activation internationale » dans Visual C++ :

- Unicode et MBCS sont activés par le biais de types de données portables dans les listes de paramètres de fonction MFC et les types de retour. Ces types sont définis de façon conditionnelle de manière appropriée, selon que votre Build définit le symbole `_UNICODE` ou le symbole `_MBCS` (ce qui signifie DBCS). Différentes variantes des bibliothèques MFC sont automatiquement liées à votre application, en fonction de ces deux symboles définis par votre Build.

- Le code de bibliothèque de classes utilise des fonctions runtime portables et d’autres moyens pour garantir un comportement Unicode ou MBCS correct.

- Vous devez toujours gérer certains genres de tâches d’internationalisation dans votre code :

  - Utilisez les mêmes fonctions runtime portables qui rendent MFC portable dans l’un ou l’autre environnement.

  - Rendre des chaînes et des caractères littéraux portables dans l’un ou l’autre environnement, à l’aide de la `_T` macro. Pour plus d’informations, consultez [mappages de texte générique dans Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

  - Prenez des précautions lors de l’analyse de chaînes sous MBCS. Ces précautions ne sont pas nécessaires sous Unicode. Pour plus d’informations, consultez [conseils de programmation MBCS](../text/mbcs-programming-tips.md).

  - Veillez à mélanger les caractères ANSI (8 bits) et Unicode (16 bits) dans votre application. Il est possible d’utiliser des caractères ANSI dans certaines parties de votre programme et des caractères Unicode dans d’autres, mais vous ne pouvez pas les mélanger dans la même chaîne.

  - Ne codez pas en dur les chaînes dans votre application. Au lieu de cela, créez-les en tant que ressources STRINGTABLE en les ajoutant au fichier. RC de l’application. Votre application peut ensuite être localisée sans nécessiter de modification ou de recompilation du code source. Pour plus d’informations sur les ressources STRINGTABLE, consultez [éditeur de chaînes](../windows/string-editor.md).

> [!NOTE]
> Les jeux de caractères européens et MBCS comportent certains caractères, tels que des lettres accentuées, avec des codes de caractères supérieurs à 0x80. Étant donné que la plupart du code utilise des caractères signés, ces caractères supérieurs à 0x80 sont étendus au moment de la conversion en **`int`** . Il s’agit d’un problème pour l’indexation de tableau, car les caractères étendus de signe, qui sont négatifs, sont indexés à l’extérieur du tableau. Les langues qui utilisent MBCS, telles que le japonais, sont également uniques. Étant donné qu’un caractère peut comporter 1 ou 2 octets, vous devez toujours manipuler les deux octets en même temps.

## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Stratégies d’internationalisation](../text/internationalization-strategies.md)
