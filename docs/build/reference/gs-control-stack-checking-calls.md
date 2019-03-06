---
title: /Gs (contrôler les appels de contrôle de pile)
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: 49433cd0c84b05248bacf1e930dd5ec78bc3cd1b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418826"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (contrôler les appels de contrôle de pile)

Contrôle le seuil pour les tests de pile.

## <a name="syntax"></a>Syntaxe

> **/Gs**[*size*]

## <a name="arguments"></a>Arguments

*size*<br/>
(Facultatif) Nombre d'octets que les variables locales peuvent occuper avant qu'une sonde de pile soit lancée. Aucun espace n’est autorisé entre **/GS** et *taille*.

## <a name="remarks"></a>Notes

Un *sonde de pile* est une séquence de code que le compilateur insère au début d’un appel de fonction. Lorsqu'elle est lancée, une sonde de pile pénètre sans heurt dans la mémoire en fonction de l'espace requis pour stocker les variables locales de la fonction. Cela entraîne le système d’exploitation vers la page en toute transparence dans la mémoire de la pile supplémentaires si nécessaire, avant que le reste de la fonction s’exécute.

Par défaut, le compilateur génère du code qui lance une sonde de pile quand une fonction requiert plus d'une page d'espace de pile. Cela équivaut à une option du compilateur **/Gs4096** pour x86, x 64, ARM, ARM64 plateformes et. Cette valeur permet à une application et au gestionnaire de mémoire Windows d’augmenter la quantité de mémoire validée dynamiquement dans la pile du programme au moment de l’exécution.

> [!NOTE]
> La valeur par défaut **/Gs4096** permet à la pile du programme d’applications pour Windows de croître correctement au moment de l’exécution. Nous vous recommandons de ne pas modifier la valeur par défaut à moins que vous sachiez exactement pourquoi vous devez la changer.

Certains programmes (par exemple, les pilotes de périphériques virtuels) n'ont pas besoin de ce mécanisme de croissance de pile par défaut. Dans ce cas, les sondes de pile ne sont pas nécessaires et vous pouvez indiquer au compilateur de les générer en définissant *taille* sur une valeur supérieure à celle qu’aucune fonction exigera pour le stockage des variables locales.

**/ Gs0** lance des tests pour chaque appel de fonction qui requiert un stockage pour les variables locales de pile. Cela peut avoir un impact négatif sur les performances.

Pour x64 cible, si le **/GS** option est spécifiée sans un *taille* argument, il est identique à **/Gs0**. Si le *taille* argument est de 1 à 9, D9014 d’avertissement est émis, et l’effet est le même que la spécification **/Gs0**.

Pour x86, ARM, ARM64 cibles et le **/GS** option sans un *taille* argument est le même que **/Gs4096**. Si le *taille* argument est de 1 à 9, D9014 d’avertissement est émis, et l’effet est le même que la spécification **/Gs4096**.

Pour toutes les cibles, un *taille* argument comprise entre 10 et 2147485647 définit le seuil à la valeur spécifiée. Un *taille* de causes 2147485648 ou supérieur, erreur irrécupérable C1049.

Vous pouvez activer ou désactiver les sondes de pile à l’aide de la [check_stack](../../preprocessor/check-stack.md) directive. **/GS** et `check_stack` pragma n’ont aucun effet sur les routines de bibliothèque C standard ; ils affectent uniquement les fonctions que vous compilez.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez le **/GS** option de compilateur et éventuellement la taille dans **des Options supplémentaires**. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
