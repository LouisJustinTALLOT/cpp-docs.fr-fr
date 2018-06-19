---
title: À l’aide des paramètres remplaçables (inscription ATL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AddReplacement
- ClearReplacements
dev_langs:
- C++
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91deabfd14d89c4a26384a14445fc51edbb3ac94
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362282"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>À l’aide des paramètres remplaçables (le bureau d’enregistrement&#39;s préprocesseur)
Paramètres remplaçables autorisent le client du bureau d’enregistrement spécifier les données de l’exécution. Pour ce faire, Registrar maintient un mappage de remplacement dans laquelle il entre les valeurs associées aux paramètres remplaçables dans votre script. Le bureau d’enregistrement effectue ces entrées au moment de l’exécution.  
  
##  <a name="_atl_using_.25.module.25"></a> À l’aide du MODULE %  
 Le [Assistant contrôle ATL](../atl/reference/atl-control-wizard.md) génère automatiquement un script qui utilise `%MODULE%`. ATL utilise ce paramètre remplaçable pour l’emplacement réel du fichier DLL ou EXE de votre serveur.  
  
## <a name="concatenating-run-time-data-with-script-data"></a>Concaténation de données de l’exécution avec les données du Script  
 Une autre utilisation du préprocesseur consiste à concaténer des données de l’exécution avec les données du script. Par exemple, une entrée est nécessaire, qui contient un chemin d’accès complet à un module avec la chaîne «`, 1`» ajouté à la fin. Tout d’abord définir l’extension suivante :  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 Ensuite, avant d’appeler une des méthodes répertoriées dans de traitement du script [appel des Scripts](../atl/invoking-scripts.md), ajoutez un remplacement à la carte :  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 Lors de l’analyse du script, Registrar développe `'%MODULE%, 1'` à `c:\mycode\mydll.dll, 1`.  
  
> [!NOTE]
>  Dans un script de Registre, 4K est la taille maximale de jeton. (Un jeton est tout élément reconnaissable de la syntaxe.) Cela inclut les jetons qui ont été créés ou développées par le préprocesseur.  
  
> [!NOTE]
>  Pour remplacer les valeurs de remplacement au moment de l’exécution, supprimez l’appel dans le script pour le [macro DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) (macro). Au lieu de cela, remplacez-le par votre propre `UpdateRegistry` méthode qui appelle [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)et passer votre tableau de **_ATL_REGMAP_ENTRY** structures. Votre tableau de **_ATL_REGMAP_ENTRY** doit avoir au moins une entrée a la valeur {**NULL**,**NULL**}, et cette entrée doit toujours être la dernière entrée. Sinon, une erreur de violation d’accès sera généré lorsque **UpdateRegistryFromResource** est appelée.  
  
> [!NOTE]
>  Lorsque vous créez un projet qui produit un fichier exécutable, ATL ajoute automatiquement des guillemets autour du nom de chemin d’accès créé au moment de l’exécution avec le **MODULE %** paramètre de script registrar. Si vous ne souhaitez pas que le nom de chemin d’accès pour inclure les guillemets, utilisez la nouvelle **MODULE_RAW %** paramètre à la place.  
>   
>  Lorsque vous créez un projet qui produit un fichier DLL, ATL n’ajoute pas de guillemets pour le nom de chemin d’accès si **MODULE %** ou **MODULE_RAW %** est utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de scripts d’inscription](../atl/creating-registrar-scripts.md)

