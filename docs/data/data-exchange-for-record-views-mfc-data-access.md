---
title: Échange de données pour les affichages des enregistrements (Accès aux données MFC)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: f9f460305b55a2313b64effdf4d1dbbfd9823def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213469"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Échange de données pour les affichages des enregistrements (Accès aux données MFC)

Quand vous utilisez [Ajouter une classe](../mfc/reference/adding-an-mfc-odbc-consumer.md) pour mapper les contrôles d’une ressource de modèle de boîte de dialogue d’une vue d’enregistrement aux champs d’un Recordset, le Framework gère l’échange de données dans les deux sens, du recordset vers les contrôles et des contrôles vers le Recordset. L'utilisation du mécanisme DDX signifie que vous n'êtes pas obligé d'écrire le code pour transférer les données d'une extrémité à une autre.

DDX pour les vues d’enregistrement fonctionne conjointement avec [RFX](../data/odbc/record-field-exchange-rfx.md) pour les recordsets de la classe `CRecordset` (ODBC).  RFX déplace les données entre l’enregistrement en cours de la source de données et les membres de données de champ d’un objet Recordset. DDX déplace les données à partir des données membres de champ vers les contrôles dans le formulaire. Cette combinaison remplit les contrôles du formulaire initialement et à mesure que l'utilisateur passe d'un enregistrement à un autre. Elle peut également retransférer les données mises à jour vers le recordset, puis vers la source de données.

L’illustration suivante montre la relation entre DDX et RFX pour les vues d’enregistrement.

![Échange&#45;de données de boîtes&#45;de dialogue et échange de champs d’enregistrement](../data/media/vc37xt1.gif "Échange&#45;de données de boîtes&#45;de dialogue et échange de champs d’enregistrement")<br/>
Échange de données de boîtes de dialogue et de champs d'enregistrements

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)
