---
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
ms.openlocfilehash: 1694d9cbc770e02c550891fc83c1cc0a9f64824a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517791"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Affichage et manipulation de données dans un formulaire

De nombreuses applications d’accès aux données sélectionnent des données et les affichent dans les champs d’un formulaire. La classe de base de données [CRecordView](../../mfc/reference/crecordview-class.md) vous donne un [CFormView](../../mfc/reference/cformview-class.md) objet directement connecté à un objet recordset. Utilise la vue d’enregistrement [échange de données de boîtes de dialogue (DDX)](../../mfc/dialog-data-exchange-and-validation.md) pour déplacer les valeurs des champs de l’enregistrement en cours à partir du recordset vers les contrôles sur le formulaire et pour replacer les informations mises à jour dans le jeu d’enregistrements. Le jeu d’enregistrements, utilise à son tour, les record field exchange (RFX) pour déplacer des données entre ses membres de données de champ et les colonnes correspondantes dans une table sur la source de données.

Vous pouvez utiliser l’Assistant Application MFC ou **ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) pour créer la classe d’affichage et sa classe de recordset associé conjointement.

La vue d’enregistrement et de son jeu d’enregistrements sont détruits lorsque vous fermez le document. Pour plus d’informations sur les vues d’enregistrements, consultez [vues d’enregistrements](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Voir aussi

[ODBC et MFC](../../data/odbc/odbc-and-mfc.md)