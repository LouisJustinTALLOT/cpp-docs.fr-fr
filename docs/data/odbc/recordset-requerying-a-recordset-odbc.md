---
description: 'En savoir plus sur : Recordset : rerequête d’un Recordset (ODBC)'
title: "Recordset : lancement d'une nouvelle requête sur un recordset (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: 3efcaac1273e6b5cc786e983bfd59f73c870cbea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204470"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Recordset : lancement d'une nouvelle requête sur un recordset (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment vous pouvez utiliser un objet Recordset pour rerequête (c’est-à-dire actualiser) lui-même à partir de la base de données et lorsque vous souhaitez le faire avec la fonction membre [Requery](../../mfc/reference/crecordset-class.md#requery) .

Les principales raisons justifiant une interrogation d’un jeu d’enregistrements sont les suivantes :

- Mettez le jeu d’enregistrements à jour en ce qui concerne les enregistrements ajoutés par vous ou par d’autres utilisateurs et les enregistrements supprimés par d’autres utilisateurs (ceux que vous supprimez sont déjà reflétés dans le jeu d’enregistrements).

- Actualisez le jeu d’enregistrements en fonction des valeurs de paramètre modifiées.

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a> Mise à jour du Recordset

Souvent, vous souhaiterez peut-être interroger votre objet Recordset pour le mettre à jour. Dans un environnement de base de données multi-utilisateur, d’autres utilisateurs peuvent apporter des modifications aux données pendant la durée de vie de votre Recordset. Pour plus d’informations sur le moment où votre recordset reflète les modifications apportées par d’autres utilisateurs et quand les recordsets des autres utilisateurs reflètent vos modifications, consultez [Recordset : comment les recordsets mettent à jour les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) et [Dynaset](../../data/odbc/dynaset.md).

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a> Rerequête basée sur de nouveaux paramètres

Une autre utilisation fréquente, et tout aussi importante, de la [rerequête](../../mfc/reference/crecordset-class.md#requery) consiste à sélectionner un nouvel ensemble d’enregistrements en fonction des valeurs de paramètre modifiées.

> [!TIP]
> La vitesse des requêtes est probablement beaucoup plus rapide si vous appelez `Requery` avec des valeurs de paramètres variables que si vous rappelez `Open` .

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a> Réinterrogeant les feuilles de réponse dynamiques et les instantanés

Étant donné que les feuilles de réponse dynamiques sont conçues pour présenter un ensemble d’enregistrements avec des données dynamiques à jour, vous souhaitez redemander les feuilles de réponse dynamiques si vous souhaitez refléter les ajouts d’autres utilisateurs. Les instantanés, quant à eux, sont utiles, car vous pouvez vous appuyer sur leur contenu statique tout en préparant les rapports, en calculant des totaux, etc. Toutefois, vous souhaiterez peut-être également interroger un instantané. Dans un environnement multi-utilisateur, les données de capture instantanée peuvent perdre la synchronisation avec la source de données à mesure que d’autres utilisateurs modifient la base de données.

#### <a name="to-requery-a-recordset-object"></a>Pour refaire une requête sur un objet Recordset

1. Appelez la fonction membre [Requery](../../mfc/reference/crecordset-class.md#requery) de l’objet.

Vous pouvez également fermer et rouvrir le Recordset d’origine. Dans les deux cas, le nouvel ensemble d’enregistrements représente l’état actuel de la source de données.

Pour obtenir un exemple, consultez [vues des enregistrements : remplissage d’une zone de liste à partir d’un second Recordset](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
> Pour optimiser `Requery` les performances, évitez de modifier le [filtre](../../data/odbc/recordset-filtering-records-odbc.md) ou le [Tri](../../data/odbc/recordset-sorting-records-odbc.md)du Recordset. Modifiez uniquement la valeur du paramètre avant d’appeler `Requery` .

Si l' `Requery` appel échoue, vous pouvez réessayer l’appel ; dans le cas contraire, votre application doit se terminer normalement. Un appel à `Requery` ou `Open` peut échouer pour plusieurs raisons. Peut-être qu’une erreur réseau se produit ; ou, pendant l’appel, une fois les données existantes libérées, mais avant l’obtention des nouvelles données, un autre utilisateur peut obtenir un accès exclusif. ou la table dont dépend votre Recordset peut être supprimée.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
