---
title: /USEPROFILE (données d’utilisation PGO avec /LTCG)
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: 7bc0033ae5ef512cbd2e2063c5cb9bd9b061c180
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317131"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (exécuter PGO en mode sans échec du thread)

Cette option de l’éditeur de liens avec [/LTCG (génération de code lien](ltcg-link-time-code-generation.md) indique à l’éditeur de liens pour générer à l’aide des données d’apprentissage de l’optimisation guidée par profil (PGO).

## <a name="syntax"></a>Syntaxe

> **/USEPROFILE**[**:**{**agressif**|**PGD =**_filename_}]

### <a name="arguments"></a>Arguments

**AGRESSIVE**<br/>
Cet argument facultatif spécifie que les optimisations de la reconnexion rapide doivent être utilisées pendant la génération de code optimisé.

**PGD**=*nom de fichier*<br/>
Spécifie un nom de fichier de base pour le fichier .pgd. Par défaut, l’éditeur de liens utilise le nom de fichier exécutable de base avec une extension .pgd.

## <a name="remarks"></a>Notes

Le **/USEPROFILE** option de l’éditeur de liens est utilisée conjointement avec **/LTCG** pour générer ou mettre à jour d’une version optimisée en fonction des données de formation PGO. Il est l’équivalent de déconseillées **/LTCG : PGUPDATE** et **/LTCG : PGOPTIMIZE** options.

Le paramètre facultatif **agressif** argument désactive relatifs à la taille des heuristiques pour tenter d’optimiser pour la vitesse. Cela peut entraîner des optimisations qui considérablement augmenter la taille de votre fichier exécutable et ne peuvent pas augmenter la vitesse qui en résulte. Vous devez profiler et comparer les résultats de l’utilisation et de ne pas à l’aide de **agressif**. Cet argument doit être spécifié explicitement ; Il n’est pas activé par défaut.

Le **PGD** argument spécifie un nom facultatif pour le fichier de .pgd des données de formation à utiliser, les mêmes que dans [/GENPROFILE ou /fastgenprofile.](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). Il est l’équivalent de déconseillées **/PGD** basculer. Par défaut, ou si aucun *filename* est spécifié, un fichier .pgd qui porte le même nom de base que le fichier exécutable est utilisé.

Le **/USEPROFILE** option de l’éditeur de liens est une nouveauté de Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **optimisation** page de propriétés.

1. Dans le **génération de Code** propriété, choisissez **utiliser génération de Code (/ LTCG)**.

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez le **/USEPROFILE** option et les arguments facultatifs dans la **des Options supplémentaires** boîte. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/GENPROFILE et /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimisations guidées par profil](../profile-guided-optimizations.md)<br/>
[Variables d’environnement pour les optimisations guidées par profil](../environment-variables-for-profile-guided-optimizations.md)<br/>
