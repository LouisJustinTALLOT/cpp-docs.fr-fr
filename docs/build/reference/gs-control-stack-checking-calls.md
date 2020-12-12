---
description: En savoir plus sur les éléments suivants:/GS (contrôler les appels de contrôle de pile)
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
ms.openlocfilehash: 128a5ad4dbcba15dfc5b76313b8576ce1448ec68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200158"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (contrôler les appels de contrôle de pile)

Contrôle le seuil pour les sondes de pile.

## <a name="syntax"></a>Syntaxe

> **/GS**[*taille*]

## <a name="arguments"></a>Arguments

*size*<br/>
(Facultatif) Nombre d'octets que les variables locales peuvent occuper avant qu'une sonde de pile soit lancée. Aucun espace n’est autorisé entre **/GS** et la *taille*.

## <a name="remarks"></a>Notes

Une *sonde de pile* est une séquence de code que le compilateur insère au début d’un appel de fonction. Lorsqu'elle est lancée, une sonde de pile pénètre sans heurt dans la mémoire en fonction de l'espace requis pour stocker les variables locales de la fonction. Le système d’exploitation pagine alors en toute transparence dans la mémoire de pile supplémentaire si nécessaire, avant que le reste de la fonction s’exécute.

Par défaut, le compilateur génère du code qui lance une sonde de pile quand une fonction requiert plus d'une page d'espace de pile. Cela équivaut à une option de compilateur **/Gs4096** pour les plateformes x86, x64, ARM et ARM64. Cette valeur permet à une application et au gestionnaire de mémoire Windows d’augmenter la quantité de mémoire validée dynamiquement dans la pile du programme au moment de l’exécution.

> [!NOTE]
> La valeur par défaut de **/Gs4096** permet à la pile du programme des applications pour Windows de croître correctement au moment de l’exécution. Nous vous recommandons de ne pas modifier la valeur par défaut à moins que vous sachiez exactement pourquoi vous devez la changer.

Certains programmes (par exemple, les pilotes de périphériques virtuels) n'ont pas besoin de ce mécanisme de croissance de pile par défaut. Dans ce cas, les sondes de pile ne sont pas nécessaires et vous pouvez empêcher le compilateur de les générer en définissant la *taille* sur une valeur supérieure à celle requise par une fonction pour le stockage des variables locales.

**/Gs0** initialise les sondes de pile pour chaque appel de fonction qui requiert le stockage pour les variables locales. Cela peut avoir un impact négatif sur les performances.

Pour les cibles x64, si l’option **/GS** est spécifiée sans argument de *taille* , elle est identique à **/Gs0**. Si la *taille* de l’argument est comprise entre 1 et 9, l’avertissement D9014 est émis et l’effet est le même que la spécification de **/Gs0**.

Pour les cibles x86, ARM et ARM64, l’option **/GS** sans argument *Size* est la même que **/Gs4096**. Si la *taille* de l’argument est comprise entre 1 et 9, l’avertissement D9014 est émis et l’effet est le même que la spécification de **/Gs4096**.

Pour toutes les cibles, un argument de *taille* compris entre 10 et 2147485647 définit le seuil à la valeur spécifiée. Une *taille* supérieure ou égale à 2147485648 provoque une erreur irrécupérable C1049.

Vous pouvez activer ou désactiver les sondes de pile à l’aide de la directive [check_stack](../../preprocessor/check-stack.md) . **/GS** et le `check_stack` pragma n’ont aucun effet sur les routines de la bibliothèque C standard ; elles affectent uniquement les fonctions que vous compilez.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Entrez l’option de compilateur **/GS** et une taille facultative dans **options supplémentaires**. Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
