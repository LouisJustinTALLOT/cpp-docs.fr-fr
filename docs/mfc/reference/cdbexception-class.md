---
title: CDBException, classe
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 755b89635eedd7808f900dc63cd3039845db1dd3
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328530"
---
# <a name="cdbexception-class"></a>CDBException, classe

Représente une condition d'exception résultant des classes de base de données.

## <a name="syntax"></a>Syntaxe

```
class CDBException : public CException
```

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CDBException::m_nRetCode](#m_nretcode)|Contient un code de retour Open Database Connectivity (ODBC), de type et RETCODE contient.|
|[CDBException::m_strError](#m_strerror)|Contient une chaîne qui décrit l’erreur en termes d’alphanumériques.|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Contient une chaîne décrivant l’erreur en termes des codes d’erreur retournée par ODBC.|

## <a name="remarks"></a>Notes

La classe inclut deux membres de données publiques que vous pouvez utiliser pour déterminer la cause de l’exception ou pour afficher un message décrivant l’exception. `CDBException` les objets sont construits et levées par les fonctions membres des classes de base de données.

> [!NOTE]
>  Cette classe est une des classes de base de données connectivité ODBC (Open) de MFC. Si vous utilisez à la place les nouvelles classes d’objets DAO (Data Access), utilisez [CDaoException](../../mfc/reference/cdaoexception-class.md) à la place. Tous les noms de classe DAO ont « CDao » comme préfixe. Pour plus d’informations, consultez l’article [vue d’ensemble : Programmation de base de données](../../data/data-access-programming-mfc-atl.md).

Les exceptions sont les cas d’exécution anormale impliquant des conditions en dehors du contrôle du programme, telles que de la source de données ou les erreurs d’e/s réseau. Les erreurs susceptibles de voir dans le cours normal de l’exécution de votre programme sont généralement pas considérés comme des exceptions.

Vous pouvez accéder à ces objets dans l’étendue d’un **CATCH** expression. Vous pouvez aussi lever `CDBException` objets à partir de votre propre code avec le `AfxThrowDBException` fonction globale.

Pour plus d’informations sur la gestion des exceptions en général, ou sur `CDBException` objets, consultez les articles [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md) et [Exceptions : Exceptions de base de données](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

##  <a name="m_nretcode"></a>  CDBException::m_nRetCode

Contient un code d’erreur de type et RETCODE contient retourné par une fonction d’API (interface) programmation ODBC application ODBC.

### <a name="remarks"></a>Notes

Ce type inclut les codes préfixée par sa SQL définies par ODBC et AFX_SQL avec le préfixe défini par les classes de base de données. Pour un `CDBException`, ce membre contient une des valeurs suivantes :

- AFX_SQL_ERROR_API_CONFORMANCE le pilote pour un `CDatabase::OpenEx` ou `CDatabase::Open` appel n’est pas conforme au niveau de conformité d’API ODBC requis 1 (SQL_OAC_LEVEL1).

- Échec de la connexion AFX_SQL_ERROR_CONNECT_FAIL à la source de données. Vous avez passé une valeur NULL`CDatabase` pointeur vers votre constructeur de jeu d’enregistrements et de la tentative suivante pour créer une connexion basée sur `GetDefaultConnect` a échoué.

- AFX_SQL_ERROR_DATA_TRUNCATED vous avez demandé plus de données que vous avez fourni pour le stockage. Pour plus d’informations sur l’augmentation du stockage de données fourni pour `CString` ou `CByteArray` des types de données, consultez le `nMaxLength` argument pour [RFX_Text](record-field-exchange-functions.md#rfx_text) et [RFX_Binary](record-field-exchange-functions.md#rfx_binary) sous « Macros et Globals. »

- Appel AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED A à `CRecordset::Open` demandant une feuille de réponse dynamique a échoué. Feuilles de réponse dynamiques ne sont pas pris en charge par le pilote.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST vous avez tenté d’ouvrir une table (ou que vous avez donné n’a pas été identifié comme un appel de procédure ou **sélectionnez** instruction), mais aucune colonne identifiée dans les appels de fonction exchange (RFX) champs d’enregistrements dans votre `DoFieldExchange` remplacer.

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH le type de RFX fonctionner dans votre `DoFieldExchange` remplacement n’est pas compatible avec le type de données de colonne dans le jeu d’enregistrements.

- AFX_SQL_ERROR_ILLEGAL_MODE vous avez appelé `CRecordset::Update` sans appeler auparavant `CRecordset::AddNew` ou `CRecordset::Edit`.

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED votre demande de verrouillage des enregistrements de mise à jour n’a pas pu être satisfaite car votre pilote ODBC ne prend pas en charge le verrouillage.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED apparaît vous avez appelé `CRecordset::Update` ou `Delete` pour une table sans clé unique et plusieurs enregistrements modifiés.

- AFX_SQL_ERROR_NO_CURRENT_RECORD vous avez tenté de modifier ou supprimer un enregistrement supprimé précédemment. Vous devez accéder à un nouvel enregistrement en cours après une suppression.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES votre demande d’une feuille de réponse dynamique n’a pas pu être satisfaite car votre pilote ODBC ne prend pas en charge les mises à jour positionnées.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED vous avez appelé `CRecordset::Update` ou `Delete`, mais lorsque l’opération a commencé l’enregistrement n’est plus est introuvable.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED une tentative de chargement de ODBC. Échec de la DLL ; Windows n’a pas été trouvé ou Impossible de charger cette DLL. Cette erreur est irrécupérable.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED que votre demande d’une feuille de réponse dynamique ne pourrait pas être satisfaite, car un pilote ODBC conforme 2 niveau est requis.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY une tentative de défilement n’a pas réussi, car la source de données ne prend pas en charge le défilement arrière.

- Appel AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED A à `CRecordset::Open` demandant une capture instantanée a échoué. Captures instantanées ne sont pas pris en charge par le pilote. (Cela doit uniquement se produire lors de la bibliothèque de curseurs ODBC ODBCCURS. DLL n’est pas présent.)

- AFX_SQL_ERROR_SQL_CONFORMANCE le pilote pour un `CDatabase::OpenEx` ou `CDatabase::Open` appel n’est pas conforme au niveau de la mise en conformité ODBC SQL requis « Minimum » (SQL_OSC_MINIMUM).

- AFX_SQL_ERROR_SQL_NO_TOTAL le pilote ODBC n’a pas pu spécifier la taille totale d’un `CLongBinary` valeur de données. L’opération a probablement échoué, car un bloc de mémoire globale n’a pas pu être préaffecté.

- AFX_SQL_ERROR_RECORDSET_READONLY vous avez tenté de mettre à jour un jeu d’enregistrements en lecture seule, ou la source de données est en lecture seule. Aucune opération de mise à jour peut être effectuée avec le jeu d’enregistrements ou `CDatabase` objet, il est associé.

- Échec de la fonction SQL_ERROR. Le message d’erreur retourné par la fonction ODBC `SQLError` est stocké dans le `m_strError` membre de données.

- SQL_INVALID_HANDLE (fonction) a échoué en raison d’un handle d’environnement non valide, un handle de connexion ou un descripteur d’instruction. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible à partir de la fonction ODBC `SQLError`.

Les codes SQL avec le préfixe sont définies par ODBC. Les codes préfixée par sa AFX sont définies dans AFXDB. H, trouvé dans MFC\INCLUDE.

##  <a name="m_strerror"></a>  CDBException::m_strError

Contient une chaîne décrivant l’erreur qui a provoqué l’exception.

### <a name="remarks"></a>Notes

La chaîne décrit l’erreur en termes d’alphanumériques. Pour plus d’informations, consultez `m_strStateNativeOrigin`.

##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin

Contient une chaîne décrivant l’erreur qui a provoqué l’exception.

### <a name="remarks"></a>Notes

La chaîne est du formulaire « état : % s, natif : % ld, origine : % s », où les codes de format, dans l’ordre, sont remplacés par les valeurs qui décrivent :

- La valeur SQLSTATE, une chaîne se terminant par null qui contient un code d’erreur à cinq caractères retournés dans le *szSqlState* paramètre de la fonction ODBC `SQLError`. Les valeurs SQLSTATE sont répertoriés dans l’annexe A, [Codes d’erreur ODBC](/previous-versions/windows/desktop/ms714687(v=vs.85)), dans le *de référence du programmeur ODBC*. Exemple : "S0022".

- Le code d’erreur natif spécifique à la source de données retournées dans le *pfNativeError* paramètre de la `SQLError` (fonction). Exemple : 207.

- Le texte de message d’erreur retourné dans le *szErrorMsg* paramètre de la `SQLError` (fonction). Ce message se compose de plusieurs noms entre crochets. En tant qu’une erreur est transmise à l’utilisateur à partir de sa source, chaque composant ODBC (source de données, pilote, le Gestionnaire de pilotes) ajoute son propre nom. Ces informations permettent d’identifier l’origine de l’erreur. Exemple : [Microsoft] [pilote ODBC SQL Server] [SQL Server]

Le framework interprète la chaîne d’erreur et met ses composants dans `m_strStateNativeOrigin`; si `m_strStateNativeOrigin` contient des informations pour plusieurs erreurs, les erreurs sont séparées par des sauts de ligne. Le framework met le texte d’erreur d’alphanumériques dans `m_strError`.

Pour plus d’informations sur les codes utilisées pour créer cette chaîne, consultez la [SQLError](/previous-versions/windows/desktop/ms716312(v=vs.85)) fonctionner dans le *de référence du programmeur ODBC*.

### <a name="example"></a>Exemple

  À partir d’ODBC : « Origine, natif : 207, état : S0022 :\[Microsoft]\[le pilote ODBC SQL Server]\[SQL Server] le nom de colonne non valide 'ColName' »

Dans `m_strStateNativeOrigin`: « Origine, natif : 207, état : S0022 :\[Microsoft]\[pilote ODBC SQL Server]\[SQL Server] »

Dans `m_strError`: « Nom de colonne non valide 'ColName' »

## <a name="see-also"></a>Voir aussi

[CException, classe](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange, classe](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException, classe](../../mfc/reference/cexception-class.md)
