---
title: Affichage et manipulation de données dans un formulaire | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3b86c58c8e5afb53cb02174beb3553378dd0efc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089364"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Affichage et manipulation de données dans un formulaire
De nombreuses applications d’accès aux données sélectionnent les données et les affichent dans les champs dans un formulaire. La classe de base de données [CRecordView](../../mfc/reference/crecordview-class.md) vous donne un [CFormView](../../mfc/reference/cformview-class.md) objet directement connecté à un objet recordset. La vue de l’enregistrement utilise [échange de données de boîtes de dialogue (DDX)](../../mfc/dialog-data-exchange-and-validation.md) pour déplacer les valeurs des champs de l’enregistrement actif du jeu d’enregistrements pour les contrôles du formulaire et pour replacer les informations mises à jour vers le recordset. L’objet recordset et utilise à son tour, échange de champs d’enregistrements (RFX) pour transférer des données entre ses membres de données de champ et les colonnes correspondantes dans une table de la source de données.  
  
 Vous pouvez utiliser l’Assistant Application MFC ou **ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) pour créer la classe d’affichage et sa classe de recordset associé conjointement.  
  
 Vue d’enregistrement et son jeu d’enregistrements sont détruits lorsque vous fermez le document. Pour plus d’informations sur les vues des enregistrements, consultez [vues des enregistrements](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC et MFC](../../data/odbc/odbc-and-mfc.md)