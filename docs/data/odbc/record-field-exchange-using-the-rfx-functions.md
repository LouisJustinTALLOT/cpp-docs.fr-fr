---
title: 'Record Field Exchange : utilisation des fonctions RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: f1afded360cfeff564f1f3d8bb9b294aa33cb733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367134"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Record Field Exchange : utilisation des fonctions RFX

Ce sujet explique comment utiliser les appels de fonction RFX qui composent le corps de votre `DoFieldExchange` remplacement.

> [!NOTE]
> Ce sujet s’applique aux classes dérivées de [CRecordset](../../mfc/reference/crecordset-class.md) dans lesquelles la chasse à la ligne en vrac n’a pas été mise en œuvre. Si vous utilisez l’extraction de lignes en bloc, l’échange de champs d’enregistrements en bloc (Bulk RFX) est implémenté. Bulk RFX est similaire à RFX. Pour comprendre les différences, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Les fonctions globales RFX échangent des données entre les colonnes sur la source de données et les membres des données sur le terrain dans votre jeu de documents. Vous écrivez les appels de fonction RFX dans la fonction [membre DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) de votre dossier. Ce sujet décrit brièvement les fonctions et montre les types de données pour lesquels les fonctions RFX sont disponibles. [Technical Note 43](../../mfc/tn043-rfx-routines.md) décrit comment écrire vos propres fonctions RFX pour des types de données supplémentaires.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Syntax fonction RFX

Chaque fonction RFX prend trois paramètres (et certains prennent un quatrième ou cinquième paramètre facultatif) :

- Un pointeur à un objet [CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Vous passez simplement `pFX` le long `DoFieldExchange`du pointeur passé à .

- Le nom de la colonne tel qu’il apparaît sur la source de données.

- Le nom du membre des données de terrain correspondant ou membre des données de paramètres dans la classe de l’enregistrement.

- (Facultatif) Dans certaines fonctions, la longueur maximale de la chaîne ou du tableau étant transférée. Cela par défaut à 255 octets, mais vous voudrez peut-être le changer. La taille maximale est basée sur `CString` la taille maximale d’un objet — **INT_MAX** (2 147 483 647) octets — mais vous rencontrerez probablement des limites de conducteur avant cette taille.

- (Facultatif) Dans `RFX_Text` la fonction, vous utilisez parfois un cinquième paramètre pour spécifier le type de données d’une colonne.

Pour plus d’informations, consultez les fonctions RFX sous [Macros et Globals](../../mfc/reference/mfc-macros-and-globals.md) dans la *référence de bibliothèque de classe*. Par exemple, lorsque vous pouvez utiliser particulièrement les paramètres, voir [Recordset: Obtaining SUMs and Other Aggregate Results (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>Types de données RFX

La bibliothèque de classe fournit des fonctions RFX pour le transfert de nombreux types de données différents entre la source de données et vos enregistrements. La liste suivante résume les fonctions RFX par type de données. Dans les cas où vous devez écrire vos propres appels de fonction RFX, sélectionnez parmi ces fonctions par type de données.

|Fonction|Type de données|
|--------------|---------------|
|`RFX_Bool`|**Bool**|
|`RFX_Byte`|**Octet**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**Flotteur**|
|`RFX_Int`|**int**|
|`RFX_Long`|**Long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Pour plus d’informations, consultez la documentation de la fonction RFX sous [Macros et Globals](../../mfc/reference/mfc-macros-and-globals.md) dans la *référence de bibliothèque de classe*. Pour plus d’informations sur la carte des types de données CMD aux types de données SQL, consultez le tableau ANSI SQL Data Types cartographiés sur les types de données CMD dans [SQL : SQL et CMD Data Types (ODBC).](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

## <a name="see-also"></a>Voir aussi

[Échange de terrain record (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset : paramétrage d'un recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset : liaison dynamique de colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Classe CFieldExchange](../../mfc/reference/cfieldexchange-class.md)
