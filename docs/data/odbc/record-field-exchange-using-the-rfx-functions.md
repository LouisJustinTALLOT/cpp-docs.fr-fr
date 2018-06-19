---
title: 'Record Field Exchange : Utilisation des fonctions RFX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1f834f9f52c8d01dbd7eb3ff54b794afc11630ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092032"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Record Field Exchange : utilisation des fonctions RFX
Cette rubrique explique comment utiliser les appels de fonction RFX qui composent le corps de votre `DoFieldExchange` remplacer.  
  
> [!NOTE]
>  Cette rubrique s’applique aux classes dérivées de [CRecordset](../../mfc/reference/crecordset-class.md) dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, RFX en bloc (RFX en bloc) est implémentée. RFX en bloc est similaire à RFX. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Les fonctions globales RFX échangent des données entre les colonnes de données source et le champ membres de données de votre recordset. Vous écrivez les appels de la fonction RFX dans le jeu d’enregistrements [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) fonction membre. Cette rubrique décrit brièvement les fonctions et présente les types de données pour laquelle RFX fonctions sont disponibles. [La Note technique 43](../../mfc/tn043-rfx-routines.md) explique comment écrire vos propres fonctions RFX pour les types de données supplémentaires.  
  
##  <a name="_core_rfx_function_syntax"></a> Syntaxe des fonctions RFX  
 Chaque fonction RFX accepte trois paramètres (et certaines prennent un paramètre optionnel de quatre ou cinq) :  
  
-   Un pointeur vers un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objet. Vous transmettez simplement le `pFX` pointeur passé à `DoFieldExchange`.  
  
-   Le nom de la colonne tel qu’il apparaît sur la source de données.  
  
-   Le nom du membre de données de champ correspondant ou membre de données de paramètre dans la classe de recordset.  
  
-   (Facultatif) Dans certaines fonctions, la longueur maximale de la chaîne ou le tableau en cours de transfert. L’emplacement par défaut est de 255 octets, mais vous souhaiterez peut-être le modifier. La taille maximale est fonction de la taille maximale d’un `CString` objet : **INT_MAX** (2 147 483 647) octets, mais vous rencontrerez probablement les limites du pilote avant que la taille.  
  
-   (Facultatif) Dans le `RFX_Text` (fonction), vous utilisez quelquefois un cinquième paramètre pour spécifier le type de données d’une colonne.  
  
 Pour plus d’informations, consultez les fonctions RFX sous [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md) dans les *Class Library Reference*. Pour obtenir un exemple de lorsque vous apportez spéciale, utilisez des paramètres, consultez [Recordset : calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).  
  
##  <a name="_core_rfx_data_types"></a> Types de données RFX  
 La bibliothèque de classes fournit les fonctions RFX pour transférer de nombreux types de données différents entre la source de données et les jeux d’enregistrements. La liste suivante résume les fonctions RFX par type de données. Dans les cas où vous devez écrire vos propres appels de fonction RFX, sélectionnez à partir de ces fonctions selon le type de données.  
  
|Fonction|Type de données|  
|--------------|---------------|  
|`RFX_Bool`|**BOOL**|  
|`RFX_Byte`|**BYTE**|  
|`RFX_Binary`|`CByteArray`|  
|`RFX_Double`|**double**|  
|`RFX_Single`|**float**|  
|`RFX_Int`|`int`|  
|`RFX_Long`|**long**|  
|`RFX_LongBinary`|`CLongBinary`|  
|`RFX_Text`|`CString`|  
|`RFX_Date`|`CTime`|  
  

 Pour plus d’informations, consultez la documentation relative aux fonctions RFX sous [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md) dans les *Class Library Reference*. Pour plus d’informations sur les types de données C++ mappent des types de données SQL, consultez le tableau de Types de ANSI SQL données mappés aux Types de données C++ dans [SQL : SQL et les Types de données C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Record Field Exchange : Fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [Recordset : Paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Recordset : Liaison dynamique de colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [Classe CRecordset](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange, classe](../../mfc/reference/cfieldexchange-class.md)