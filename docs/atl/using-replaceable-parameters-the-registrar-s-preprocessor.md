---
description: "En savoir plus sur : utilisation des paramètres remplaçables (le préprocesseur du Bureau d'&#39;s)"
title: Utilisation de paramètres remplaçables (ATL Registrar)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 5b8b8071115186a462bbf9ca0b12d869458dd925
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157200"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Utilisation de paramètres remplaçables (le préprocesseur du Bureau d'&#39;s)

Les paramètres remplaçables permettent au client d’un bureau d’enregistrement de spécifier des données au moment de l’exécution. Pour ce faire, le Bureau d’enregistrement conserve un mappage de remplacement dans lequel il entre les valeurs associées aux paramètres remplaçables dans votre script. Le Bureau d’enregistrement effectue ces entrées au moment de l’exécution.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a> Utilisation de% MODULE%

L' [Assistant contrôle ATL](../atl/reference/atl-control-wizard.md) génère automatiquement un script qui utilise `%MODULE%` . ATL utilise ce paramètre remplaçable pour l’emplacement réel de la DLL ou de l’EXE de votre serveur.

## <a name="concatenating-run-time-data-with-script-data"></a>Concaténation de données de Run-Time avec des données de script

Une autre utilisation du préprocesseur consiste à concaténer les données d’exécution avec les données de script. Par exemple, supposons qu’une entrée qui contient un chemin d’accès complet à un module avec la chaîne « `, 1` » soit ajoutée à la fin. Tout d’abord, définissez le développement suivant :

```rgs
'MySampleKey' = s '%MODULE%, 1'
```

Puis, avant d’appeler l’une des méthodes de traitement de script listées dans [appel de scripts](../atl/invoking-scripts.md), ajoutez un remplacement à la carte :

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Pendant l’analyse du script, le Bureau d’enregistrement s’étend `'%MODULE%, 1'` à `c:\mycode\mydll.dll, 1` .

> [!NOTE]
> Dans un script d’inscription, 4K est la taille de jeton maximale. (Un jeton est un élément reconnaissable dans la syntaxe.) Cela comprend les jetons qui ont été créés ou développés par le préprocesseur.

> [!NOTE]
> Pour remplacer les valeurs de remplacement au moment de l’exécution, supprimez l’appel du script à la macro [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) . Au lieu de cela, remplacez-le par votre propre `UpdateRegistry` méthode qui appelle [CAtlModule :: UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule :: UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources), et transmettez votre tableau de structures de _ATL_REGMAP_ENTRY. Votre tableau de _ATL_REGMAP_ENTRY doit avoir au moins une entrée ayant la valeur {NULL, NULL}, et cette entrée doit toujours être la dernière entrée. Dans le cas contraire, une erreur de violation d’accès sera générée lorsque `UpdateRegistryFromResource` est appelé.

> [!NOTE]
> Lors de la génération d’un projet qui génère un exécutable, ATL ajoute automatiquement des guillemets autour du nom du chemin d’accès créé au moment de l’exécution avec le paramètre de script **% module%** Registrar. Si vous ne souhaitez pas que le nom du chemin d’accès inclue les guillemets, utilisez le nouveau paramètre **% MODULE_RAW%** à la place.
>
> Lors de la génération d’un projet qui génère une DLL, ATL n’ajoute pas de guillemets au nom du chemin d’accès si **% module%** ou **% MODULE_RAW%** est utilisé.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)
