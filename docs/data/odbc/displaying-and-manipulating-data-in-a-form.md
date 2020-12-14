---
description: En savoir plus sur l’affichage et la manipulation des données dans un formulaire
title: Affichage et manipulation de données dans un formulaire
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: 151e4036830f4923fbed2e609535edf3beacee5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252322"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Affichage et manipulation de données dans un formulaire

De nombreuses applications d’accès aux données sélectionnent des données et les affichent dans des champs d’un formulaire. La classe de base de données [CRecordView](../../mfc/reference/crecordview-class.md) vous donne un objet [CFormView](../../mfc/reference/cformview-class.md) directement connecté à un objet Recordset. La vue de l’enregistrement utilise l' [échange de données de boîtes de dialogue (DDX)](../../mfc/dialog-data-exchange-and-validation.md) pour déplacer les valeurs des champs de l’enregistrement actuel à partir du recordset vers les contrôles du formulaire et pour déplacer les informations mises à jour vers le Recordset. À son tour, le recordset utilise RFX (Record Field Exchange) pour déplacer des données entre ses membres de données de champ et les colonnes correspondantes dans une table sur la source de données.

Vous pouvez utiliser l’Assistant Application MFC ou **Ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) pour créer conjointement la classe de vue et sa classe de Recordset associée.

La vue de l’enregistrement et son Recordset sont détruits lorsque vous fermez le document. Pour plus d’informations sur les vues des enregistrements, consultez [vues des enregistrements](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Voir aussi

[ODBC et MFC](../../data/odbc/odbc-and-mfc.md)
