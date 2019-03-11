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
ms.openlocfilehash: 22f2dba49e894e93cb6791d76a65730f3269199e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748006"
---
# <a name="international-enabling"></a>Compatibilité internationale

La plupart des code C et C++ sur les hypothèses sur la manipulation de caractère et de chaîne qui ne fonctionnent pas correctement dans les applications internationales. Bien que MFC et la bibliothèque Runtime prennent en charge Unicode ou MBCS, il reste encore à faire. Pour vous guider, cette section explique la signification de « compatibilité internationale » dans Visual C++ :

- Unicode et MBCS sont activés au moyen des types de données portables dans les listes de paramètres de fonction MFC et types de retour. Ces types sont définis de façon conditionnelle de la façon appropriée, selon que votre compilation définit le symbole `_UNICODE` ou le symbole `_MBCS` (ce qui signifie DBCS). Variantes différentes pour les bibliothèques MFC sont automatiquement liés à votre application, en fonction de ces deux symboles définit votre build.

- Code de bibliothèque de classes utilise des fonctions runtime portables et autres méthodes pour garantir le comportement Unicode ou MBCS.

- Vous devez toujours gérer certains types de tâches d’internationalisation dans votre code :

   - Utilisez les mêmes fonctions runtime portables qui rendent MFC portable sous les deux environnements.

   - Améliorer la portabilité sous les deux environnements, des chaînes littérales et les caractères à l’aide de la `_T` (macro). Pour plus d’informations, consultez [des mappages de texte générique dans tchar.h](../text/generic-text-mappings-in-tchar-h.md).

   - Prenez des précautions lors de l’analyse de chaînes sous MBCS. Ces précautions ne sont pas nécessaires sous Unicode. Pour plus d’informations, consultez [conseils de programmation de MBCS](../text/mbcs-programming-tips.md).

   - Faites attention lorsque vous mélangez ANSI (8 bits) et les caractères Unicode (16 bits) dans votre application. Il est possible d’utiliser des caractères ANSI dans certaines parties de votre programme et des caractères Unicode dans d’autres, mais vous ne pouvez pas les mélanger dans la même chaîne.

   - Ne les chaînes pas coder en dur dans votre application. Au lieu de cela, vérifiez les ressources STRINGTABLE en les ajoutant au fichier .rc de l’application. Votre application peut ensuite être localisée sans nécessiter de modifications du code source ou la recompilation. Pour plus d’informations sur les ressources STRINGTABLE, consultez [éditeur de chaînes](../windows/string-editor.md).

> [!NOTE]
>  Les jeux de caractères d’Europe et MBCS ont certains caractères, tels que les lettres accentuées, avec des codes de caractère supérieurs à 0 x 80. Étant donné que la plupart du code utilise des caractères signés, ces caractères supérieurs à 0 x 80 sont étendu avec un signe lorsqu’il est converti en **int**. Il s’agit d’un problème pour l’indexation de tableau, car les caractères de signe étendu, qui est négatif, index en dehors du tableau. Les langues qui utilisent MBCS, telles que le japonais, sont également uniques. Car un caractère peut se composer de 1 ou 2 octets, vous devez toujours manipuler les deux octets en même temps.

## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Stratégies d’internationalisation](../text/internationalization-strategies.md)
