---
title: 'Record Field Exchange : Utilisation de RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 2a029f653753363e08b3c4f8b9fceab6295924af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395649"
---
# <a name="record-field-exchange-using-rfx"></a>Record Field Exchange : Utilisation de RFX

Cette rubrique explique comment pour utiliser RFX en relation avec ce que fait le framework.

> [!NOTE]
>  Cette rubrique s’applique aux classes dérivées de [CRecordset](../../mfc/reference/crecordset-class.md) dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, RFX en bloc (RFX en bloc) est implémentée. RFX en bloc est similaire à RFX. Pour comprendre les différences, consultez [jeu d’enregistrements : Extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Les rubriques suivantes contiennent des informations connexes :

- [Record Field Exchange : Utilisation de l’Assistant Code](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) présente les principaux composants de RFX et explique le code que l’Assistant Application MFC et **ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) écrire pour prendre en charge RFX et la façon dont vous souhaiterez peut-être modifier le code de l’Assistant.

- [Record Field Exchange : Utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) explique écrire les appels aux fonctions RFX dans votre `DoFieldExchange` remplacer.

Le tableau suivant indique le rôle par rapport à ce que l’infrastructure effectue pour vous.

### <a name="using-rfx-you-and-the-framework"></a>Utilisation de RFX : Vous et l’infrastructure

|Vous|L'infrastructure|
|---------|-------------------|
|Déclarez vos classes de jeu d’enregistrements avec un Assistant. Spécifiez les noms et types de données des membres de données de champ.|L’Assistant dérive un `CRecordset` classe et les écritures un [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) remplacer pour vous, y compris un RFX appel pour chaque membre de données de champ de fonction.|
|(Facultatif) Ajouter manuellement des membres de données de paramètre nécessaire à la classe. Ajouter manuellement un appel de fonction RFX à `DoFieldExchange` pour chaque membre de données de paramètre, ajoutez un appel à [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) pour le groupe de paramètres et spécifiez le nombre total de paramètres dans [m_nParams ](../../mfc/reference/crecordset-class.md#m_nparams). Consultez [jeu d’enregistrements : Paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|(Facultatif) Lier manuellement les colonnes supplémentaires aux membres de données de champ. Incrémenter manuellement [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Consultez [jeu d’enregistrements : Liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Construisez un objet de votre classe de jeu d’enregistrements. Avant d’utiliser l’objet, définissez les valeurs de son paramètre données membres, le cas échéant.|Pour plus d’efficacité, l’infrastructure lie au préalable les paramètres à l’aide de ODBC. Lorsque vous transmettez des valeurs de paramètre, l’infrastructure les passe à la source de données. Seules les valeurs de paramètre sont envoyées pour des actualisations, sauf si les chaînes de tri et/ou de filtre ont été modifiés.|
|Ouvrez un objet de jeu d’enregistrements à l’aide [CRecordset::Open](../../mfc/reference/crecordset-class.md#open).|Exécute la requête du recordset, lie les colonnes aux membres de données de champ du jeu d’enregistrements et les appels `DoFieldExchange` pour échanger des données entre le premier enregistrement sélectionné et les membres de données de champ du jeu d’enregistrements.|
|Défilement dans le jeu d’enregistrements à l’aide [CRecordset::Move](../../mfc/reference/crecordset-class.md#move) ou une commande de menu ou de barre d’outils.|Appels `DoFieldExchange` pour transférer des données vers les membres de données de champ du nouvel enregistrement en cours.|
|Ajouter, mettre à jour et supprimer des enregistrements.|Appels `DoFieldExchange` pour transférer des données à la source de données.|

## <a name="see-also"></a>Voir aussi

[Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Record Field Exchange : Fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset : Calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange, classe](../../mfc/reference/cfieldexchange-class.md)<br/>
[Macros, fonctions globales et Variables globales](../../mfc/reference/mfc-macros-and-globals.md)

