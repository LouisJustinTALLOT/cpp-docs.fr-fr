---
description: En savoir plus sur:/USEPROFILE (exécuter PGO en mode thread-safe)
title: /USEPROFILE (utiliser les données PGO avec LTCG)
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: c6c293b8467ea308dc2f7b4a4cd916cc5d9ac4c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247044"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (exécuter PGO en mode thread-safe)

Cette option de l’éditeur de liens avec [/LTCG (génération de code durant l’édition de liens](ltcg-link-time-code-generation.md) indique à l’éditeur de liens de générer à l’aide des données d’apprentissage de l’optimisation guidée par profil (PGO).

## <a name="syntax"></a>Syntaxe

> **/USEPROFILE**[**:**{ | **PGD agressif =**_nom_fichier_}]

### <a name="arguments"></a>Arguments

**FAÇON**<br/>
Cet argument facultatif spécifie que des optimisations de vitesse agressives doivent être utilisées lors de la génération de code optimisé.

**PGD** = *nom du fichier*<br/>
Spécifie un nom de fichier de base pour le fichier .pgd. Par défaut, l’éditeur de liens utilise le nom de fichier exécutable de base avec une extension. pgd.

## <a name="remarks"></a>Notes

L’option **/USEPROFILE** de l’éditeur de liens est utilisée avec **/LTCG** pour générer ou mettre à jour une build optimisée basée sur les données d’apprentissage PGO. C’est l’équivalent des options **/LTCG : PGUPDATE** et **/LTCG : PGOPTIMIZE** déconseillées.

L’argument **agressif** facultatif désactive les heuristiques relatives à la taille pour tenter d’optimiser la vitesse. Cela peut entraîner des optimisations qui augmentent considérablement la taille de votre fichier exécutable et peuvent ne pas augmenter la vitesse résultante. Vous devez Profiler et comparer les résultats de à l’aide de et de ne pas utiliser **agressif**. Cet argument doit être spécifié explicitement ; elle n’est pas activée par défaut.

L’argument **PGD** spécifie un nom facultatif pour le fichier d’apprentissage Data. pgd à utiliser, le même que dans [/GENPROFILE ou/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). C’est l’équivalent du commutateur **/PGD** déconseillé. Par défaut, ou si aucun *nom* de fichier n’est spécifié, un fichier. pgd portant le même nom de base que l’exécutable est utilisé.

L’option de l’éditeur de liens **/USEPROFILE** est une nouveauté de Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Dans la propriété **génération de code durant l’édition de liens** , choisissez utiliser la **génération de code durant l’édition de liens (/LTCG)**.

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Entrez l’option **/USEPROFILE** et les arguments facultatifs dans la zone **options supplémentaires** . Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/GENPROFILE et/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimisations guidées par profil](../profile-guided-optimizations.md)<br/>
[Variables d’environnement pour les optimisations de Profile-Guided](../environment-variables-for-profile-guided-optimizations.md)<br/>
