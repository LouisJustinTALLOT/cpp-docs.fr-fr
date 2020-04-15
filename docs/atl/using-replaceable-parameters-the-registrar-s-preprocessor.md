---
title: Utilisation de paramètres remplaçables (registraire ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 2474db2de384baa9113ed39aef4d3d9c9048903d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329227"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Utilisation de paramètres remplaçables (Le registraire&#39;s Preprocessor)

Les paramètres remplaçables permettent au client d’un registraire de spécifier les données en temps de fonctionnement. Pour ce faire, le registraire maintient une carte de remplacement dans laquelle il entre les valeurs associées aux paramètres remplaçables de votre script. Le registraire fait ces entrées au moment de l’exécution.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>Utilisation de %MODULE%

Le [assistant de contrôle ATL](../atl/reference/atl-control-wizard.md) génère `%MODULE%`automatiquement un script qui utilise . ATL utilise ce paramètre remplaçable pour l’emplacement réel du DLL ou EXE de votre serveur.

## <a name="concatenating-run-time-data-with-script-data"></a>Concatenating Run-Time Data avec script Data

Une autre utilisation du préprocesseur est de concatenate des données de temps d’exécution avec des données de script. Supposons, par exemple, qu’une entrée soit nécessaire qui`, 1`contient un chemin complet vers un module avec la chaîne « » annexée à la fin. Tout d’abord, définir l’expansion suivante :

```
'MySampleKey' = s '%MODULE%, 1'
```

Puis, avant d’appeler l’une des méthodes de traitement de script énumérées dans [l’invocation des scripts](../atl/invoking-scripts.md), ajouter un remplacement à la carte:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Pendant l’analyse du script, le `'%MODULE%, 1'` registraire `c:\mycode\mydll.dll, 1`s’étend à .

> [!NOTE]
> Dans un script de registraire, 4K est la taille maximale des jetons. (Un jeton est tout élément reconnaissable dans la syntaxe.) Cela comprend les jetons qui ont été créés ou élargis par le préprocesseur.

> [!NOTE]
> Pour remplacer les valeurs de remplacement au moment de l’exécution, supprimez l’appel dans le script à la [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) macro. Au lieu de cela, remplacez-le par votre propre `UpdateRegistry` méthode qui appelle [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources), et passez votre gamme de structures _ATL_REGMAP_ENTRY. Votre tableau de _ATL_REGMAP_ENTRY doit avoir au moins une entrée qui est définie à 'NULL,NULL', et cette entrée doit toujours être la dernière entrée. Dans le cas contraire, une `UpdateRegistryFromResource` erreur de violation d’accès sera générée lorsqu’elle est appelée.

> [!NOTE]
> Lors de la construction d’un projet qui extraie un exécutant, ATL ajoute automatiquement des guillemets autour du nom de voie créé au moment de l’exécution avec le paramètre de script de registraire **%MODULE%.** Si vous ne voulez pas que le nom du chemin inclue les guillemets, utilisez plutôt le nouveau paramètre **% MODULE_RAW %.**
>
> Lors de la construction d’un projet qui produit un DLL, ATL n’ajoutera pas de guillemets au nom du chemin si **%MODULE%** ou **%MODULE_RAW%** est utilisé.

## <a name="see-also"></a>Voir aussi

[Création de scripts registraires](../atl/creating-registrar-scripts.md)
