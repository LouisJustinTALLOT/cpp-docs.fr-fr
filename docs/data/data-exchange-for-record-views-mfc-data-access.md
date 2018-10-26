---
title: Échange de données pour les vues d’enregistrements (accès de données MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b6b0109baaf17f804a0ea15eff2e9e766196b86
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052803"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Échange de données pour les affichages des enregistrements (Accès aux données MFC)

Lorsque vous utilisez [ajouter une classe](../mfc/reference/adding-an-mfc-odbc-consumer.md) pour mapper les contrôles dans la ressource de modèle de boîte de dialogue d’une vue d’enregistrement aux champs d’un recordset, l’infrastructure gère l’échange de données dans les deux sens : du recordset vers les contrôles et des contrôles vers le recordset. L'utilisation du mécanisme DDX signifie que vous n'êtes pas obligé d'écrire le code pour transférer les données d'une extrémité à une autre.

Le mécanisme DDX des vues des enregistrements fonctionne en association avec [RFX](../data/odbc/record-field-exchange-rfx.md) pour les recordsets de la classe `CRecordset` (ODBC).  RFX déplace les données entre l’enregistrement actif de la source de données et les membres de données de champ d’un objet recordset. DDX déplace les données à partir des données membres de champ vers les contrôles dans le formulaire. Cette combinaison remplit les contrôles du formulaire initialement et à mesure que l'utilisateur passe d'un enregistrement à un autre. Elle peut également retransférer les données mises à jour vers le recordset, puis vers la source de données.

La figure suivante montre la relation entre DDX et RFX pour les vues d’enregistrements.

![Boîte de dialogue&#45;échange de données et enregistrement&#45;champ exchange](../data/media/vc37xt1.gif "vc37xt1")<br/>
Échange de données de boîtes de dialogue et de champs d'enregistrements

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)