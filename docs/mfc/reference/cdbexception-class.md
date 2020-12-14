---
description: 'En savoir plus sur : CDBException, classe'
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
ms.openlocfilehash: 8e337cc0f66a4a281de07ba3839895096e8021d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222123"
---
# <a name="cdbexception-class"></a>CDBException, classe

Représente une condition d'exception résultant des classes de base de données.

## <a name="syntax"></a>Syntaxe

```
class CDBException : public CException
```

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDBException :: m_nRetCode](#m_nretcode)|Contient un code de retour Open Database Connectivity (ODBC) de type RETCODE.|
|[CDBException :: m_strError](#m_strerror)|Contient une chaîne qui décrit l’erreur en termes alphanumériques.|
|[CDBException :: m_strStateNativeOrigin](#m_strstatenativeorigin)|Contient une chaîne décrivant l’erreur en termes de codes d’erreur retournés par ODBC.|

## <a name="remarks"></a>Notes

La classe comprend deux membres de données publics que vous pouvez utiliser pour déterminer la cause de l’exception ou pour afficher un message texte décrivant l’exception. `CDBException` les objets sont construits et levés par les fonctions membres des classes de base de données.

> [!NOTE]
> Cette classe est l’une des classes Open Database Connectivity (ODBC) de MFC. Si vous utilisez à la place les classes DAO (Data Access Objects) les plus récentes, utilisez [CDaoException](../../mfc/reference/cdaoexception-class.md) à la place. Tous les noms de classes DAO portent le préfixe « CDao ». Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de bases de données](../../data/data-access-programming-mfc-atl.md).

Les exceptions sont des cas d’exécution anormale impliquant des conditions en dehors du contrôle du programme, telles que des erreurs de source de données ou d’e/s réseau. Les erreurs que vous pouvez vous attendre à rencontrer dans le cadre d’une exécution normale de votre programme ne sont généralement pas considérées comme des exceptions.

Vous pouvez accéder à ces objets dans l’étendue d’une expression **catch** . Vous pouvez également lever `CDBException` des objets à partir de votre propre code avec la `AfxThrowDBException` fonction globale.

Pour plus d’informations sur la gestion des exceptions en général, ou sur `CDBException` les objets, consultez les articles sur la [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md) et [exceptions : bases de données](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXDB. h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a> CDBException :: m_nRetCode

Contient un code d’erreur ODBC de type RETCODE retourné par une fonction d’interface de programmation d’applications (API) ODBC.

### <a name="remarks"></a>Notes

Ce type comprend des codes préfixés SQL définis par ODBC et des codes préfixés par AFX_SQL définis par les classes de base de données. Pour un `CDBException` , ce membre doit contenir l’une des valeurs suivantes :

- AFX_SQL_ERROR_API_CONFORMANCE le pilote d’un `CDatabase::OpenEx` `CDatabase::Open` appel ou n’est pas conforme au niveau de conformité de l’API ODBC requis (SQL_OAC_LEVEL1).

- AFX_SQL_ERROR_CONNECT_FAIL connexion à la source de données a échoué. Vous avez passé un `CDatabase` pointeur null à votre constructeur Recordset et la tentative suivante de création d’une connexion basée sur `GetDefaultConnect` a échoué.

- AFX_SQL_ERROR_DATA_TRUNCATED vous avez demandé plus de données que vous n’avez fourni le stockage pour. Pour plus d’informations sur l’amélioration du stockage de données fourni pour les `CString` `CByteArray` types de données ou, consultez l' `nMaxLength` argument pour [RFX_Text](record-field-exchange-functions.md#rfx_text) et [RFX_Binary](record-field-exchange-functions.md#rfx_binary) sous « macros et globales ».

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED un appel à la `CRecordset::Open` demande d’une feuille de réponse dynamique a échoué. Les feuilles de réponse dynamiques ne sont pas prises en charge par le pilote.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST vous avez tenté d’ouvrir une table (ou ce que vous avez donné n’a pas pu être identifié en tant qu’appel de procédure ou instruction **Select** ), mais aucune colonne n’est identifiée dans les appels de fonction RFX (Record Field Exchange) dans votre `DoFieldExchange` remplacement.

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH le type d’une fonction RFX dans votre `DoFieldExchange` remplacement n’est pas compatible avec le type de données de la colonne dans le jeu d’enregistrements.

- AFX_SQL_ERROR_ILLEGAL_MODE vous avez appelé `CRecordset::Update` sans appeler `CRecordset::AddNew` ou `CRecordset::Edit` .

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED votre demande de verrouillage des enregistrements pour la mise à jour n’a pas pu être satisfaite car votre pilote ODBC ne prend pas en charge le verrouillage.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED vous avez appelé `CRecordset::Update` ou `Delete` pour une table sans clé unique et modifié plusieurs enregistrements.

- AFX_SQL_ERROR_NO_CURRENT_RECORD vous avez tenté de modifier ou de supprimer un enregistrement précédemment supprimé. Vous devez faire défiler jusqu’à un nouvel enregistrement actif après une suppression.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES votre demande de feuille de réponse dynamique n’a pas pu être satisfaite car votre pilote ODBC ne prend pas en charge les mises à jour positionnées.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED vous avez appelé `CRecordset::Update` ou `Delete` , mais lorsque l’opération a commencé, l’enregistrement est introuvable.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED une tentative de chargement de la ODBC.DLL a échoué ; Windows n’a pas pu trouver ou n’a pas pu charger cette DLL. Cette erreur est irrécupérable.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED votre demande de feuille de réponse dynamique n’a pas pu être satisfaite car un pilote ODBC conforme au niveau 2 est requis.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY une tentative de défilement a échoué, car la source de données ne prend pas en charge le défilement arrière.

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED un appel à `CRecordset::Open` la demande d’un instantané a échoué. Les instantanés ne sont pas pris en charge par le pilote. (Cela ne doit se produire que lorsque la bibliothèque de curseurs ODBC ODBCCURS.DLL n’est pas présente.)

- AFX_SQL_ERROR_SQL_CONFORMANCE le pilote d’un `CDatabase::OpenEx` `CDatabase::Open` appel ou n’est pas conforme au niveau de conformité SQL ODBC requis « minimum » (SQL_OSC_MINIMUM).

- AFX_SQL_ERROR_SQL_NO_TOTAL le pilote ODBC n’a pas pu spécifier la taille totale d’une `CLongBinary` valeur de données. L’opération a probablement échoué car un bloc de mémoire globale n’a pas pu être préalloué.

- AFX_SQL_ERROR_RECORDSET_READONLY vous avez tenté de mettre à jour un jeu d’enregistrements en lecture seule, ou la source de données est en lecture seule. Aucune opération de mise à jour ne peut être effectuée avec le recordset ou l' `CDatabase` objet auquel il est associé.

- Échec de la fonction SQL_ERROR. Le message d’erreur retourné par la fonction ODBC `SQLError` est stocké dans le `m_strError` membre de données.

- Échec de la fonction SQL_INVALID_HANDLE en raison d’un handle d’environnement, d’un handle de connexion ou d’un handle d’instruction non valide. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible à partir de la fonction ODBC `SQLError` .

Les codes préfixés SQL sont définis par ODBC. Les codes préfixés AFX sont définis dans AFXDB. H, trouvé dans MFC\INCLUDE.

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a> CDBException :: m_strError

Contient une chaîne décrivant l’erreur qui a provoqué l’exception.

### <a name="remarks"></a>Notes

La chaîne décrit l’erreur en termes alphanumériques. Pour obtenir des informations plus détaillées et un exemple, consultez `m_strStateNativeOrigin` .

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a> CDBException :: m_strStateNativeOrigin

Contient une chaîne décrivant l’erreur qui a provoqué l’exception.

### <a name="remarks"></a>Notes

La chaîne se présente sous la forme « État :% s, natif :% LD, origine :% s », où les codes de format, dans l’ordre, sont remplacés par des valeurs qui décrivent :

- SQLSTATE, une chaîne se terminant par un caractère null qui contient un code d’erreur à cinq caractères retourné dans le paramètre *szSqlState* de la fonction ODBC `SQLError` . Les valeurs SQLSTATE sont répertoriées dans l’annexe A, [codes d’erreur ODBC](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes), dans le *Guide de référence du programmeur ODBC*. Exemple : « S0022 ».

- Code d’erreur natif, propre à la source de données, retourné dans le paramètre *pfNativeError* de la `SQLError` fonction. Exemple : 207.

- Texte du message d’erreur retourné dans le paramètre *szErrorMsg* de la `SQLError` fonction. Ce message est constitué de plusieurs noms entre crochets. Comme une erreur est transmise à partir de sa source à l’utilisateur, chaque composant ODBC (source de données, pilote, gestionnaire de pilotes) ajoute son propre nom. Ces informations permettent d’identifier l’origine de l’erreur. Exemple : [Microsoft] [pilote ODBC SQL Server] [SQL Server]

Le Framework interprète la chaîne d’erreur et place ses composants dans `m_strStateNativeOrigin` ; si `m_strStateNativeOrigin` contient des informations pour plusieurs erreurs, les erreurs sont séparées par des sauts de lignes. Le Framework place le texte d’erreur alphanumérique dans `m_strError` .

Pour plus d’informations sur les codes utilisés pour créer cette chaîne, consultez la fonction [SQLError](/sql/odbc/reference/syntax/sqlerror-function) dans le *Guide de référence du programmeur ODBC*.

### <a name="example"></a>Exemple

À partir de ODBC : « État : S0022, Native : 207, origine : \[ Microsoft] \[ ODBC SQL Server Driver] \[ SQL Server] nom de colonne non valide «colname »

Dans `m_strStateNativeOrigin` : « État : S0022, Native : 207, origine : \[ Microsoft] \[ ODBC SQL Server Driver] \[ SQL Server] »

Dans `m_strError` : « nom de colonne non valide’colname' »

## <a name="see-also"></a>Voir aussi

[CException (classe)](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange, classe](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset :: Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset ::D supprim](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException (classe)](../../mfc/reference/cexception-class.md)
