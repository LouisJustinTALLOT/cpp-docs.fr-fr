---
title: "Recordset : lancement d'une nouvelle requête sur un recordset (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: cdae28f81eebe8427bc829072e0d9a83c6ec1722
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366946"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Recordset : lancement d'une nouvelle requête sur un recordset (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Ce sujet explique comment vous pouvez utiliser un objet de la liste d’enregistrement pour requery (c’est-à-dire, actualiser) lui-même à partir de la base de données et quand vous voudrez peut-être le faire avec la fonction membre [Requery.](../../mfc/reference/crecordset-class.md#requery)

Les principales raisons de la reconquérir d’un registre sont les suivantes :

- Mettre l’ensemble d’enregistrements à jour en ce qui concerne les enregistrements ajoutés par vous ou par d’autres utilisateurs et les enregistrements supprimés par d’autres utilisateurs (ceux que vous supprimez sont déjà reflétés dans le jeu d’enregistrements).

- Rafraîchir le registre en fonction de l’évolution des valeurs de paramètres.

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Mettre le Recordet à jour

Fréquemment, vous voudrez requery votre objet de la liste de disques pour le mettre à jour. Dans un environnement de base de données multiusage, d’autres utilisateurs peuvent apporter des modifications aux données pendant la durée de vie de votre jeu d’enregistrement. Pour plus d’informations sur le moment où votre dossier reflète les modifications apportées par d’autres utilisateurs et lorsque les enregistrements d’autres utilisateurs reflètent vos modifications, voir [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) et [Dynaset](../../data/odbc/dynaset.md).

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Requerying basé sur de nouveaux paramètres

Une autre utilisation fréquente — et tout aussi importante — de [Requery](../../mfc/reference/crecordset-class.md#requery) consiste à sélectionner un nouvel ensemble de records en fonction de l’évolution des valeurs des paramètres.

> [!TIP]
> La vitesse de requête est `Requery` probablement beaucoup plus rapide `Open` si vous appelez avec des valeurs de paramètres changeantes que si vous appelez à nouveau.

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Requerying Dynasets vs Snapshots

Parce que les dynasets sont destinés à présenter un ensemble d’enregistrements avec des données dynamiques à jour, vous voulez requery dynasets souvent si vous voulez refléter les ajouts d’autres utilisateurs. Les instantanés, d’autre part, sont utiles parce que vous pouvez compter en toute sécurité sur leur contenu statique pendant que vous préparez des rapports, calculez les totaux, et ainsi de suite. Pourtant, vous pourriez parfois envie de requery un instantané ainsi. Dans un environnement multiuscule, les données instantanées peuvent perdre la synchronisation avec la source de données à mesure que d’autres utilisateurs modifient la base de données.

#### <a name="to-requery-a-recordset-object"></a>Pour requery un objet recordet

1. Appelez la fonction membre [Requery](../../mfc/reference/crecordset-class.md#requery) de l’objet.

Alternativement, vous pouvez fermer et rouvrir le recordet d’origine. Dans les deux cas, le nouveau dossier représente l’état actuel de la source de données.

Par exemple, voir [Vues d’enregistrement : Remplir une boîte de liste à partir d’un deuxième enregistrement](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
> Pour optimiser `Requery` les performances, évitez de modifier le filtre ou le [tri](../../data/odbc/recordset-sorting-records-odbc.md)du [recordet.](../../data/odbc/recordset-filtering-records-odbc.md) Modifier uniquement la valeur `Requery`du paramètre avant d’appeler .

Si `Requery` l’appel échoue, vous pouvez rejuger l’appel; autrement, votre demande devrait se terminer gracieusement. Un appel `Requery` `Open` ou pourrait échouer pour l’une ou l’autre des raisons. Peut-être qu’une erreur de réseau se produit; ou, pendant l’appel, après la publication des données existantes, mais avant l’obtention des nouvelles données, un autre utilisateur peut obtenir un accès exclusif; ou le tableau sur lequel dépend votre dossier pourrait être supprimé.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : liaison dynamique de colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
