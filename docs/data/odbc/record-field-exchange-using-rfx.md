---
title: 'Record Field Exchange : utilisation de RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: dc0cdcee758f4842b0738068a8a11c4e2e404155
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367143"
---
# <a name="record-field-exchange-using-rfx"></a>Record Field Exchange : utilisation de RFX

Ce sujet explique ce que vous faites pour utiliser RFX par rapport à ce que fait le cadre.

> [!NOTE]
> Ce sujet s’applique aux classes dérivées de [CRecordset](../../mfc/reference/crecordset-class.md) dans lesquelles la chasse à la ligne en vrac n’a pas été mise en œuvre. Si vous utilisez l’extraction de lignes en bloc, l’échange de champs d’enregistrements en bloc (Bulk RFX) est implémenté. Bulk RFX est similaire à RFX. Pour comprendre les différences, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Les sujets suivants contiennent des informations connexes :

- [Record Field Exchange: Working with the Wizard Code](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) introduit les principaux composants de RFX et explique le code que le MFC Application Wizard and Add **Class** (tel que décrit dans [l’ajout d’un MFC ODBC Consumer](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) écrire pour prendre en charge RFX et comment vous pourriez vouloir modifier le code assistant.

- [Échange de champ d’enregistrement : L’utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) explique l’écriture d’appels vers les fonctions RFX dans votre `DoFieldExchange` remplacement.

Le tableau suivant montre votre rôle par rapport à ce que le cadre fait pour vous.

### <a name="using-rfx-you-and-the-framework"></a>Utilisation de RFX: Vous et le Cadre

|Vous|L'infrastructure|
|---------|-------------------|
|Déclarez vos cours de recordet avec un magicien. Spécifier les noms et les types de données des membres des données sur le terrain.|L’assistant dérive `CRecordset` une classe et écrit un remplacement [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) pour vous, y compris un appel de fonction RFX pour chaque membre de données sur le terrain.|
|(Facultatif) Ajoutez manuellement tous les membres des données de paramètres nécessaires à la classe. Ajoutez manuellement un appel de `DoFieldExchange` fonction RFX pour chaque membre des données de paramètres, ajoutez un appel à [CFieldExchange : : SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) pour le groupe de paramètres, et spécifiez le nombre total de paramètres dans [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Voir [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|(Facultatif) Lier manuellement des colonnes supplémentaires aux membres des données sur le terrain. Augmentation manuelle [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Voir [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Construisez un objet de votre classe de recordet. Avant d’utiliser l’objet, définissez les valeurs de ses membres de données de paramètres, le cas échéant.|Pour plus d’efficacité, le cadre prébine les paramètres, à l’aide d’ODBC. Lorsque vous transmettez les valeurs de paramètres, le cadre les transmet à la source de données. Seules les valeurs de paramètres sont envoyées pour les requeries, à moins que le tri et/ou les chaînes de filtre n’aient changé.|
|Ouvrez un objet recordet à l’aide [de CRecordset::Open](../../mfc/reference/crecordset-class.md#open).|Exécute la requête du recordet, lie les colonnes aux membres des `DoFieldExchange` données de champ du jeu d’enregistrement et appelle à échanger des données entre le premier enregistrement sélectionné et les membres de données sur le terrain du groupe d’enregistrement.|
|Faites défiler le jeu d’enregistrements à l’aide [de CRecordset : Move](../../mfc/reference/crecordset-class.md#move) ou un menu ou une commande de barre d’outils.|Appels `DoFieldExchange` à transférer des données aux membres des données sur le terrain à partir du nouvel enregistrement actuel.|
|Ajouter, mettre à jour et supprimer des enregistrements.|Appels `DoFieldExchange` pour transférer des données à la source de données.|

## <a name="see-also"></a>Voir aussi

[Échange de terrain record (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset : calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Classe CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[Macros, fonctions globales et variables globales](../../mfc/reference/mfc-macros-and-globals.md)
