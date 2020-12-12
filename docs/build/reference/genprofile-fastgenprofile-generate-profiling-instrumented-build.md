---
description: En savoir plus sur:/GENPROFILE,/FASTGENPROFILE (générer la génération instrumentée de profilage)
title: /GENPROFILE, /FASTGENPROFILE (Générer une build instrumentée de profilage)
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: 7bb0f9b1c7a6036c5e721f79b438bf9dd6504111
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200232"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE (Générer une build instrumentée de profilage)

Spécifie la génération d’un fichier .pgd par l’éditeur de liens pour prendre en charge l’optimisation guidée par profil. **/GENPROFILE** et **/FASTGENPROFILE** utilisent des paramètres par défaut différents. Utilisez **/GENPROFILE** pour privilégier la précision sur la vitesse et l’utilisation de la mémoire pendant le profilage. Utilisez **/FASTGENPROFILE** pour favoriser une utilisation plus réduite de la mémoire et une vitesse supérieure à la précision.

## <a name="syntax"></a>Syntaxe

> **/GENPROFILE** \[ **:**{ \[ **COUNTER32** \| **COUNTER64**] \| \[ **exact** \| **noexact**] \| **MEMMAX =** _#_ \| **MEMMIN =** _#_ \| \[ **chemin** \| **nopath**] \| \[ **TRACKEH** \| **NOTRACKEH** ] \| **PGD =**_filename_}] \
> **/FASTGENPROFILE** \[ **:**{ \[ **COUNTER32** \| **COUNTER64**] \| \[ **exact** \| **noexact**] \| **MEMMAX =** _#_ \| **MEMMIN =** _#_ \| [**chemin** \| **nopath** ] \| \[ **TRACKEH** \| **NOTRACKEH** ] \| **PGD =**_filename_}]

### <a name="arguments"></a>Arguments

Les arguments suivants peuvent être spécifiés pour **/GENPROFILE** ou **/FASTGENPROFILE**. Les arguments répertoriés ici séparés par un caractère de barre verticale ( **|** ) s’excluent mutuellement. Utilisez une virgule (**,**) pour séparer les options.

**COUNTER32** &#124; **COUNTER64**<br/>
Utilisez **COUNTER32** pour spécifier l’utilisation des compteurs de sonde 32 bits et **COUNTER64** pour spécifier des compteurs de sonde 64 bits. Lorsque vous spécifiez **/GENPROFILE**, la valeur par défaut est **COUNTER64**. Lorsque vous spécifiez **/FASTGENPROFILE**, la valeur par défaut est **COUNTER32**.

**Exact** &#124; **noexact**<br/>
Utilisez **exact** pour spécifier des incréments de verrouillage thread-safe pour les sondes. **Noexact** spécifie les opérations d’incrément non protégées pour les sondes. La valeur par défaut est **noexact**.

**MEMMAX** = *valeur*,  = *valeur* MEMMIN<br/>
Utilisez **MEMMAX** et **MEMMIN** pour spécifier les tailles de réservation maximale et minimale pour les données d’apprentissage en mémoire. La valeur est la quantité de mémoire à réserver en octets. Par défaut, ces valeurs sont déterminées par une méthode heuristique interne.

**Chemin d’accès**  &#124; **nopath** <br/>
Utilisez **path**  pour spécifier un ensemble distinct de compteurs PGO pour chaque chemin d’accès unique à une fonction. Utilisez **nopath**  pour spécifier un seul ensemble de compteurs pour chaque fonction. Lorsque vous spécifiez **/GENPROFILE**, la valeur par défaut est **path** . Lorsque vous spécifiez **/FASTGENPROFILE**, la valeur par défaut est **nopath** .

**TRACKEH**  &#124; **NOTRACKEH** <br/>
Spécifie s’il faut utiliser des compteurs supplémentaires pour conserver un décompte précis quand des exceptions sont levées au cours de l’apprentissage. Utilisez **TRACKEH**  pour spécifier des compteurs supplémentaires pour un nombre exact. Utilisez **NOTRACKEH**  pour spécifier des compteurs uniques pour le code qui n’utilise pas la gestion des exceptions ou qui ne rencontrent pas d’exceptions dans vos scénarios d’apprentissage.  Lorsque vous spécifiez **/GENPROFILE**, la valeur par défaut est **TRACKEH** . Lorsque vous spécifiez **/FASTGENPROFILE**, la valeur par défaut est **NOTRACKEH** .

**PGD** = *nom du fichier*<br/>
Spécifie un nom de fichier de base pour le fichier .pgd. Par défaut, l’éditeur de liens utilise le nom du fichier image exécutable de base avec une extension .pgd.

## <a name="remarks"></a>Notes

Les options **/GENPROFILE** et **/FASTGENPROFILE** indiquent à l’éditeur de liens de générer le fichier d’instrumentation de profilage nécessaire pour prendre en charge la formation des applications pour l’optimisation guidée par profil (PGO). Ces options sont nouvelles dans Visual Studio 2015. Privilégiez ces options pour les options **/LTCG : PGINSTRUMENT**, **/PGD** et **/POGOSAFEMODE** déconseillées, ainsi que les variables d’environnement **POGOSAFEMODE**, **VCPROFILE_ALLOC_SCALE** et **VCPROFILE_PATH** . Les informations de profilage générées par l’apprentissage de l’application sont utilisées comme entrée pour effectuer les optimisations de la totalité du programme ciblé pendant les générations. Vous pouvez définir des options supplémentaires pour contrôler différentes fonctionnalités de profilage pour les performances pendant l’apprentissage de l’application et les builds. Les options par défaut spécifiées par **/GENPROFILE** donnent des résultats plus précis, en particulier pour les grandes applications multithread complexes. L’option **/FASTGENPROFILE** utilise des valeurs par défaut différentes pour un encombrement mémoire plus faible et des performances plus rapides pendant l’apprentissage, au détriment de la précision.

Les informations de profilage sont capturées lorsque vous exécutez l’application instrumentée après la génération à l’aide de **/GENPROFILE** de **/FASTGENPROFILE**. Ces informations sont capturées lorsque vous spécifiez l’option de l’éditeur de liens [/USEPROFILE](useprofile.md) pour effectuer l’étape de profilage, puis utilisées pour guider l’étape de génération optimisée. Pour plus d’informations sur la façon d’effectuer l’apprentissage de votre application et des détails sur les données collectées, consultez [optimisations guidées par profil](../profile-guided-optimizations.md).

Vous devez également spécifier **/LTCG** quand vous spécifiez **/GENPROFILE** ou **/FASTGENPROFILE**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Entrez les options et les arguments **/GENPROFILE** ou **/FASTGENPROFILE** dans la zone **options supplémentaires** . Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/LTCG (génération de code durant l’édition de liens)](ltcg-link-time-code-generation.md)<br/>
