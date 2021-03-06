---
description: 'En savoir plus sur : vues des enregistrements (accès aux données MFC)'
title: Vues d'enregistrements (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
ms.openlocfilehash: 098a45c0bff0dfaf1aba83f12dddad9a5f943638
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319051"
---
# <a name="record-views--mfc-data-access"></a>Vues d'enregistrements (Accès aux données MFC)

Cette section s’applique uniquement aux classes ODBC MFC. Pour plus d’informations sur OLE DB vues des enregistrements, consultez [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) et [utilisation des vues d’enregistrement OLE DB](../data/oledb/using-ole-db-record-views.md).

Pour prendre en charge les applications d’accès aux données basées sur les formulaires, la bibliothèque de classes fournit la classe [CRecordView](../mfc/reference/crecordview-class.md). Une vue d’enregistrement est un objet de vue de formulaire dont les contrôles sont mappés directement aux membres de données de champ d’un objet [Recordset](../data/odbc/recordset-odbc.md) (et indirectement aux colonnes correspondantes dans un résultat de requête ou une table de la source de données). Comme sa classe de base [CFormView](../mfc/reference/cformview-class.md), `CRecordView` est basé sur une ressource de modèle de boîte de dialogue.

## <a name="form-uses"></a>Utilisations des formulaires

Les formulaires sont utiles pour diverses tâches d’accès aux données :

- Saisie de données

- Exécution de l'analyse des données en lecture seule

- Mise à jour des données

## <a name="further-reading-about-record-views"></a>Informations complémentaires sur les vues d'enregistrements

Le contenu de ces rubriques s'applique aux classes ODBC et DAO. Utilisez `CRecordView` pour ODBC et `CDaoRecordView` pour DAO.

Les sujets abordés sont les suivants :

- [Fonctionnalités des classes d'affichage des enregistrements](../data/features-of-record-view-classes-mfc-data-access.md)

- [Échange de données pour les vues des enregistrements](../data/data-exchange-for-record-views-mfc-data-access.md)

- [Votre rôle dans l'utilisation d'une vue de l'enregistrement](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)

- [Conception et création d'une vue de l'enregistrement](../data/designing-and-creating-a-record-view-mfc-data-access.md)

- [Utilisation d'une vue de l'enregistrement](../data/using-a-record-view-mfc-data-access.md)

## <a name="see-also"></a>Voir aussi

[Programmation de l’accès aux données (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[Liste des pilotes ODBC](../data/odbc/odbc-driver-list.md)
