---
title: 'Recordset : Actualisant un Recordset (ODBC) | Microsoft Docs'
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
ms.openlocfilehash: d043045823806453d509e91e61284fadd5326d23
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340714"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Recordset : lancement d'une nouvelle requête sur un recordset (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique comment vous pouvez utiliser un objet recordset à requery (Actualiser) à partir de la base de données et lorsque vous souhaiterez peut-être le faire avec le [Requery](../../mfc/reference/crecordset-class.md#requery) fonction membre.  
  
 Les principales raisons pour l’actualisation d’un jeu d’enregistrements sont :  
  
-   Mettre le recordset à jour en ce qui concerne les enregistrements ajoutés par vous ou par d’autres utilisateurs et les enregistrements supprimés par d’autres utilisateurs (ceux que vous supprimez sont déjà reflétées dans le jeu d’enregistrements).  
  
-   Actualiser le jeu d’enregistrements basé sur la modification des valeurs de paramètre.  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a> Mise à jour le jeu d’enregistrements  
 Souvent, vous devez actualiser votre objet de jeu d’enregistrements pour le mettre à jour. Dans un environnement de base de données multi-utilisateur, d’autres utilisateurs peuvent apporter des modifications aux données pendant la durée de vie de votre jeu d’enregistrements. Pour plus d’informations sur quand votre recordset reflète les modifications apportées par d’autres utilisateurs et quand les recordsets des autres utilisateurs reflètent vos modifications, consultez [Recordset : mise à jour des enregistrements par les Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) et [Dynaset](../../data/odbc/dynaset.md).  
  
##  <a name="_core_requerying_based_on_new_parameters"></a> Réexécutez la requête basée sur les nouveaux paramètres  
 Une autre utilisation fréquente et il est tout aussi important, utilisez de [Requery](../../mfc/reference/crecordset-class.md#requery) consiste à sélectionner un nouveau jeu d’enregistrements basé sur la modification des valeurs de paramètre.  
  
> [!TIP]
>  Vitesse de la requête est sans doute beaucoup plus rapide si vous appelez `Requery` avec modification des valeurs de paramètre que si vous appelez `Open` à nouveau.  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> Actualisant les Dynasets vs. Snapshots  
 Étant donné que les feuilles de réponse dynamiques sont censées présenter un ensemble d’enregistrements avec des données à jour dynamiques, vous souhaitez vous lanciez souvent si vous souhaitez refléter les ajouts d’autres utilisateurs. Captures instantanées, quant à eux, sont utiles, car vous pouvez en toute sécurité s’appuient sur leur contenu statique lors de la préparation des États, calculer des totaux et ainsi de suite. Cependant, il est parfois utile actualiser un instantané. Dans un environnement multi-utilisateur, données de capture instantanée peuvent perdre la synchronisation avec la source de données comme les autres utilisateurs modifier la base de données.  
  
#### <a name="to-requery-a-recordset-object"></a>Pour actualiser un objet recordset  
  
1.  Appelez le [Requery](../../mfc/reference/crecordset-class.md#requery) fonction membre de l’objet.  
  
 Vous pouvez également fermer et rouvrir le jeu d’enregistrements d’origine. Dans les deux cas, le nouveau jeu d’enregistrements représente l’état actuel de la source de données.  
  
 Pour obtenir un exemple, consultez [vues d’enregistrements : remplissage d’une zone de liste à partir d’un Second Recordset](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
> [!TIP]
>  Pour optimiser les `Requery` performances, évitez de modifier le jeu d’enregistrements [filtre](../../data/odbc/recordset-filtering-records-odbc.md) ou [tri](../../data/odbc/recordset-sorting-records-odbc.md). Modifier uniquement la valeur du paramètre avant d’appeler `Requery`.  
  
 Si le `Requery` appeler échoue, vous pouvez réessayer l’appel ; sinon, votre application se termine normalement. Un appel à `Requery` ou `Open` peut échouer pour plusieurs raisons. Par exemple, une erreur réseau se produit ; ou, lors de l’appel, une fois que les données existantes sont libérées, mais avant que les nouvelles données sont obtenues, un autre utilisateur peut obtenir l’accès exclusif ; ou la table dont dépend votre jeu d’enregistrements peut être supprimée.  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)