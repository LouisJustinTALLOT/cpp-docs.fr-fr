---
title: À l’aide des paramètres remplaçables (inscription ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 1c772c0493b351d8452400a4fb1e3949ab6f28f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274142"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>À l’aide des paramètres remplaçables (le bureau d’enregistrement&#39;s préprocesseur)

Paramètres remplaçables autoriser le client du bureau d’enregistrement spécifier les données d’exécution. Pour ce faire, le bureau d’enregistrement gère un mappage de remplacement dans laquelle il entre les valeurs associées aux paramètres remplaçables dans votre script. Le bureau d’enregistrement effectue ces entrées au moment de l’exécution.

##  <a name="_atl_using_.25.module.25"></a> À l’aide du MODULE %

Le [Assistant contrôle ATL](../atl/reference/atl-control-wizard.md) génère automatiquement un script qui utilise `%MODULE%`. ATL utilise ce paramètre remplaçable pour l’emplacement réel du fichier DLL ou EXE de votre serveur.

## <a name="concatenating-run-time-data-with-script-data"></a>Concaténation de données d’exécution avec des données de Script

Une autre utilisation du préprocesseur consiste à concaténer les données d’exécution avec des données de script. Par exemple, une entrée est nécessaire, qui contient un chemin d’accès complet à un module avec la chaîne «`, 1`» est ajoutée à la fin. Tout d’abord, définissez l’expansion suivante :

```
'MySampleKey' = s '%MODULE%, 1'
```

Ensuite, avant d’appeler une des méthodes répertoriées dans de traitement du script [appel des Scripts](../atl/invoking-scripts.md), ajoutez un remplacement à la carte :

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Lors de l’analyse du script, le bureau d’enregistrement développe `'%MODULE%, 1'` à `c:\mycode\mydll.dll, 1`.

> [!NOTE]
>  Dans un script de bureau d’enregistrement, 4K est la taille maximale de jeton. (Un jeton est tout élément reconnaissable de la syntaxe.) Cela inclut les jetons qui ont été créés ou développés par le préprocesseur.

> [!NOTE]
>  Pour remplacer les valeurs de remplacement en cours d’exécution, supprimez l’appel dans le script pour le [macro DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) macro. Au lieu de cela, le remplacer par votre propre `UpdateRegistry` méthode qui appelle [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)et passer votre tableau de _ATL_REGMAP_ Structures d’entrée. Votre tableau de _ATL_REGMAP_ENTRY doit avoir au moins une entrée a la valeur {NULL, NULL}, et cette entrée doit toujours être la dernière entrée. Sinon, une erreur de violation d’accès sera généré lorsque `UpdateRegistryFromResource` est appelée.

> [!NOTE]
>  Lorsque vous créez un projet qui produit un fichier exécutable, ATL ajoute automatiquement des guillemets autour du nom de chemin d’accès créé au moment de l’exécution avec le **MODULE %** paramètre de script de bureau d’enregistrement. Si vous ne souhaitez pas que le nom de chemin d’accès pour inclure les guillemets, utiliser la nouvelle **% MODULE_RAW %** paramètre à la place.
>
>  Lorsque vous créez un projet qui génère une DLL, ATL n’ajoute pas de guillemets dans le nom de chemin si **MODULE %** ou **% MODULE_RAW %** est utilisé.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)
