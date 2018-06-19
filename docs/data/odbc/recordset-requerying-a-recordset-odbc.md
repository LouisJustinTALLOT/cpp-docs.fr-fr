---
title: 'Recordset : Actualisant un Recordset (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3157f416cf6fb7e0fd3b5ad4797b83de218c9ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091574"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Recordset : lancement d'une nouvelle requête sur un recordset (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique comment vous pouvez utiliser un objet recordset pour actualiser (Actualiser) à partir de la base de données et lorsque vous souhaiterez peut-être le faire avec la [Requery](../../mfc/reference/crecordset-class.md#requery) fonction membre.  
  
 Les principales raisons pour l’actualisation d’un jeu d’enregistrements sont :  
  
-   Mettre le recordset à jour en ce qui concerne les enregistrements ajoutés par vous ou par d’autres utilisateurs et aux enregistrements supprimés par d’autres utilisateurs (ceux que vous supprimez sont déjà pris en compte dans le jeu d’enregistrements).  
  
-   Actualiser le jeu d’enregistrements basé sur la modification des valeurs de paramètre.  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a> Mise à jour le jeu d’enregistrements  
 Souvent, vous devez actualiser votre objet recordset pour le mettre à jour. Dans un environnement de base de données multi-utilisateur, d’autres utilisateurs peuvent apporter des modifications aux données pendant la durée de vie de votre recordset. Pour plus d’informations sur quand votre recordset reflète les modifications apportées par d’autres utilisateurs et quand les recordsets des autres utilisateurs reflètent vos modifications, consultez [Recordset : modification des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) et [Dynaset](../../data/odbc/dynaset.md).  
  
##  <a name="_core_requerying_based_on_new_parameters"></a> Réexécutez la requête basée sur les nouveaux paramètres  
 Une autre utilisation fréquente et il est tout aussi important : utilisation de [Requery](../../mfc/reference/crecordset-class.md#requery) consiste à sélectionner un nouvel ensemble d’enregistrements en fonction des modifications de valeurs de paramètre.  
  
> [!TIP]
>  Vitesse des requêtes est probablement beaucoup plus rapide si vous appelez **Requery** avec la modification de valeurs de paramètre que si vous appelez **ouvrir** à nouveau.  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> Réexécutez la requête et de feuilles de réponse dynamiques. Snapshots  
 Étant donné que les feuilles de réponse dynamiques sont censées présenter un ensemble d’enregistrements avec des données à jour dynamiques, vous souhaitez vous lanciez souvent si vous souhaitez refléter les ajouts d’autres utilisateurs. Captures instantanées, quant à eux, sont utiles, car vous pouvez en toute sécurité s’appuient sur leur contenu statique pendant que vous préparez des rapports, calculez des totaux et ainsi de suite. Néanmoins, vous souhaiterez parfois actualiser un instantané. Dans un environnement multi-utilisateur, les données de capture instantanée peuvent perdre la synchronisation avec la source de données lorsque les autres utilisateurs modifient la base de données.  
  
#### <a name="to-requery-a-recordset-object"></a>Pour actualiser un objet recordset  
  
1.  Appelez le [Requery](../../mfc/reference/crecordset-class.md#requery) fonction membre de l’objet.  
  
 Vous pouvez également fermer et rouvrir le jeu d’enregistrements d’origine. Dans les deux cas, le nouveau jeu d’enregistrements représente l’état actuel de la source de données.  
  
 Pour obtenir un exemple, consultez [vues des enregistrements : remplissage d’une zone de liste à partir d’un Second Recordset](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
> [!TIP]
>  Pour optimiser les **Requery** les performances, évitez de modifier le jeu d’enregistrements [filtre](../../data/odbc/recordset-filtering-records-odbc.md) ou [tri](../../data/odbc/recordset-sorting-records-odbc.md). Modifiez uniquement la valeur du paramètre avant d’appeler **Requery**.  
  
 Si le **Requery** appel échoue, vous pouvez réessayer l’appel ; sinon, votre application se termine normalement. Un appel à **Requery** ou **ouvrir** peut échouer pour plusieurs raisons. Par exemple, une erreur réseau se produit ; ou bien, lors de l’appel, après la publication de données existantes, mais avant que les nouvelles données sont obtenues, un autre utilisateur peut obtenir l’accès exclusif ; ou la table dont dépend le jeu d’enregistrements peut être supprimée.  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Liaison dynamique de colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)