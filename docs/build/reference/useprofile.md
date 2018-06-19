---
title: /USEPROFILE (données d’utilisation PGO avec /LTCG) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- USEPROFILE
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156a571eaa3db31b8c5345f1550346503651665d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377991"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (PGO exécuter en mode sans échec du thread)

Cette option de l’éditeur de liens avec [/LTCG (génération de code de lien](ltcg-link-time-code-generation.md) indique à l’éditeur de liens pour générer à l’aide de données d’apprentissage de l’optimisation guidée par profil (PGO).

## <a name="syntax"></a>Syntaxe

> **/USEPROFILE**[**:**{**agressif**|**PGD =**_nom de fichier_}]

### <a name="arguments"></a>Arguments

**AGRESSIF**<br/>
Cet argument facultatif spécifie que les optimisations de vitesse agressif doivent être utilisées lors de la génération de code optimisé.

**PGD**=*nom de fichier*<br/>
Spécifie un nom de fichier de base pour le fichier .pgd. Par défaut, l’éditeur de liens utilise le nom de fichier exécutable de base avec une extension .pgd.

## <a name="remarks"></a>Notes

Le **/useprofile** option de l’éditeur de liens est utilisée avec **LTCG** pour générer ou mettre à jour d’une version optimisée en fonction des données de formation PGO. Il est l’équivalent de déconseillées **/LTCG : PGUPDATE** et **/LTCG : PGOPTIMIZE** options.

Le paramètre facultatif **agressif** argument désactive liés à la taille des heuristiques pour tente d’optimiser la vitesse. Cela peut entraîner des optimisations qui sensiblement augmentent la taille de votre fichier exécutable et ne peuvent pas augmenter la vitesse qui en résulte. Vous devez profiler et comparer les résultats de l’utilisation et de ne pas à l’aide de **agressif**. Cet argument doit être spécifié explicitement ; Il n’est pas activé par défaut.

Le **PGD** argument spécifie un nom facultatif pour le fichier de .pgd de données d’apprentissage à utiliser, les mêmes que dans [/GENPROFILE ou /fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). Il est l’équivalent de déconseillées **/PGD** basculer. Par défaut, ou si aucun *nom de fichier* est spécifié, un fichier .pgd qui a le même nom que le fichier exécutable est utilisé.

Le **/useprofile** option de l’éditeur de liens est une nouveauté de Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **optimisation** page de propriétés.

1. Dans le **génération de Code** propriété, choisissez **utiliser génération de Code (/ LTCG)**.

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez le **/useprofile** option et les arguments facultatifs dans la **des Options supplémentaires** boîte. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/GENPROFILE et /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md)<br/>
[Variables d’environnement pour les optimisations guidées par profil](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
