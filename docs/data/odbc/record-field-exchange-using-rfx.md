---
title: 'Record Field Exchange : utilisation de RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 70197d2a9130388e86bb94f0d670360bb35febeb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075869"
---
# <a name="record-field-exchange-using-rfx"></a>Record Field Exchange : utilisation de RFX

Cette rubrique explique ce que vous faites pour utiliser RFX par rapport à ce que fait l’infrastructure.

> [!NOTE]
>  Cette rubrique s’applique aux classes dérivées de [CRecordset](../../mfc/reference/crecordset-class.md) dans lesquelles l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, l’échange de champs d’enregistrements en bloc (Bulk RFX) est implémenté. Bulk RFX est similaire à RFX. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Les rubriques suivantes contiennent des informations connexes :

- [Record Field Exchange : l’utilisation du code](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) de l’Assistant présente les principaux composants de RFX et explique le code que l’Assistant Application MFC et l’Assistant **Ajout de classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) écrivent pour prendre en charge RFX et comment vous pouvez modifier le code de l’Assistant.

- [Record Field Exchange : l’utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) explique comment écrire des appels aux fonctions RFX dans votre remplacement de `DoFieldExchange`.

Le tableau suivant indique votre rôle par rapport à ce que l’infrastructure fait pour vous.

### <a name="using-rfx-you-and-the-framework"></a>Utilisation de RFX : vous et l’infrastructure

|Vous|L'infrastructure|
|---------|-------------------|
|Déclarez vos classes d’ensemble d’enregistrements avec un Assistant. Spécifiez les noms et les types de données des membres de données de champ.|L’Assistant dérive une classe `CRecordset` et écrit une substitution [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) pour vous, y compris un appel de fonction RFX pour chaque membre de données de champ.|
|Facultatif Ajoutez manuellement les membres de données de paramètre nécessaires à la classe. Ajoutez manuellement un appel de fonction RFX à `DoFieldExchange` pour chaque membre de données de paramètre, ajoutez un appel à [CFieldExchange :: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) pour le groupe de paramètres et spécifiez le nombre total de paramètres dans [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|Facultatif Lier manuellement des colonnes supplémentaires aux membres de données de champ. Incrémentez manuellement [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Consultez [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Construisez un objet de votre classe Recordset. Avant d’utiliser l’objet, définissez les valeurs de ses membres de données de paramètre, le cas échéant.|Pour des performances optimales, l’infrastructure prélie les paramètres à l’aide d’ODBC. Lorsque vous transmettez des valeurs de paramètre, l’infrastructure les passe à la source de données. Seules les valeurs de paramètre sont envoyées pour les rerequêtes, à moins que les chaînes de tri et/ou de filtre aient changé.|
|Ouvrez un objet Recordset à l’aide de [CRecordset :: Open](../../mfc/reference/crecordset-class.md#open).|Exécute la requête du Recordset, lie des colonnes à des données membres de champ du Recordset et appelle `DoFieldExchange` pour échanger des données entre le premier enregistrement sélectionné et les membres de données de champ du Recordset.|
|Faites défiler le recordset à l’aide de [CRecordset :: Move](../../mfc/reference/crecordset-class.md#move) ou d’une commande de menu ou de barre d’outils.|Appelle `DoFieldExchange` pour transférer des données vers les membres de données de champ à partir du nouvel enregistrement en cours.|
|Ajouter, mettre à jour et supprimer des enregistrements.|Appelle `DoFieldExchange` pour transférer des données à la source de données.|

## <a name="see-also"></a>Voir aussi

[Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset : calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange, classe](../../mfc/reference/cfieldexchange-class.md)<br/>
[Macros, fonctions globales et variables globales](../../mfc/reference/mfc-macros-and-globals.md)
