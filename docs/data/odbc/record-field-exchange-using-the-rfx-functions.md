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
ms.openlocfilehash: 4d621fbe2207114dd51845b819d309802a009690
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216529"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Record Field Exchange : utilisation des fonctions RFX

Cette rubrique explique comment utiliser les appels de fonction RFX qui composent le corps de votre `DoFieldExchange` remplacement.

> [!NOTE]
> Cette rubrique s’applique aux classes dérivées de [CRecordset](../../mfc/reference/crecordset-class.md) dans lesquelles l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, l’échange de champs d’enregistrements en bloc (Bulk RFX) est implémenté. Bulk RFX est similaire à RFX. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Les fonctions globales RFX échangent des données entre les colonnes de la source de données et les données membres de champ dans votre Recordset. Vous écrivez les appels de fonction RFX dans la fonction membre [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) de votre Recordset. Cette rubrique décrit brièvement les fonctions et indique les types de données pour lesquels les fonctions RFX sont disponibles. La [note technique 43](../../mfc/tn043-rfx-routines.md) décrit comment écrire vos propres fonctions RFX pour des types de données supplémentaires.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Syntaxe des fonctions RFX

Chaque fonction RFX prend trois paramètres (et certains prennent un quatrième ou cinquième paramètre facultatif) :

- Pointeur vers un objet [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Vous transmettez simplement le `pFX` pointeur transmis à `DoFieldExchange` .

- Nom de la colonne tel qu’il apparaît dans la source de données.

- Nom du membre de données de champ ou du membre de données de paramètre correspondant dans la classe du Recordset.

- Facultatif Dans certaines fonctions, la longueur maximale de la chaîne ou du tableau en cours de transfert. La valeur par défaut est de 255 octets, mais vous pouvez le modifier. La taille maximale est basée sur la taille maximale d’un `CString` objet ( **INT_MAX** (2 147 483 647) octets), mais vous rencontrerez probablement des limites de pilote avant cette taille.

- Facultatif Dans la `RFX_Text` fonction, vous utilisez parfois un cinquième paramètre pour spécifier le type de données d’une colonne.

Pour plus d’informations, consultez les fonctions RFX sous [macros et globales](../../mfc/reference/mfc-macros-and-globals.md) dans la référence de la *bibliothèque de classes*. Pour obtenir un exemple d’utilisation particulière des paramètres, consultez [Recordset : obtention de sommes et d’autres résultats d’agrégation (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>Types de données RFX

La bibliothèque de classes fournit des fonctions RFX pour transférer de nombreux types de données différents entre la source de données et vos recordsets. La liste suivante récapitule les fonctions RFX par type de données. Dans les cas où vous devez écrire vos propres appels de fonction RFX, sélectionnez à partir de ces fonctions par type de données.

|Fonction|Type de données|
|--------------|---------------|
|`RFX_Bool`|**Boolean**|
|`RFX_Byte`|**POIDS**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**`double`**|
|`RFX_Single`|**`float`**|
|`RFX_Int`|**`int`**|
|`RFX_Long`|**`long`**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Pour plus d’informations, consultez la documentation sur les fonctions RFX sous [macros et globales](../../mfc/reference/mfc-macros-and-globals.md) dans la référence de la *bibliothèque de classes*. Pour plus d’informations sur la façon dont les types de données C++ mappent aux types de données SQL, consultez la table types de données SQL ANSI mappés aux types de données C++ dans [SQL : types de données SQL et c++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Voir aussi

[RFX (Record Field Exchange)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange, classe](../../mfc/reference/cfieldexchange-class.md)
