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
ms.openlocfilehash: 1ab7daeb3af55c92985c951c632b1d4050681474
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321890"
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
|[CDBException::m_nRetCode](#m_nretcode)|Contient un code de retour de connectivité à base de données ouverte (ODBC), de type RETCODE.|
|[CDBException::m_strError](#m_strerror)|Contient une chaîne qui décrit l’erreur en termes alphanumériques.|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Contient une chaîne décrivant l’erreur en termes de codes d’erreur retournés par ODBC.|

## <a name="remarks"></a>Notes

La classe comprend deux membres de données publiques que vous pouvez utiliser pour déterminer la cause de l’exception ou pour afficher un message texte décrivant l’exception. `CDBException`les objets sont construits et jetés par les fonctions des membres des classes de base de données.

> [!NOTE]
> Cette classe est l’une des classes de connectivité à base de données ouvertes (ODBC) de MFC. Si vous utilisez plutôt les nouvelles classes d’objets d’accès aux données (DAO), utilisez [CDaoException](../../mfc/reference/cdaoexception-class.md) à la place. Tous les noms de classe DAO ont "CDao" comme préfixe. Pour plus d’informations, voir l’article [Aperçu: Programmation de base de données](../../data/data-access-programming-mfc-atl.md).

Les exceptions sont des cas d’exécution anormale impliquant des conditions en dehors du contrôle du programme, telles que la source de données ou le réseau I /O erreurs. Les erreurs que vous pourriez vous attendre à voir dans le cours normal de l’exécution de votre programme ne sont généralement pas considérées comme des exceptions.

Vous pouvez accéder à ces objets dans le cadre d’une expression **CATCH.** Vous pouvez `CDBException` également jeter des objets `AfxThrowDBException` de votre propre code avec la fonction globale.

Pour plus d’informations sur le `CDBException` traitement des exceptions en général, ou sur les objets, voir les articles [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md) et [Exceptions: Database Exceptions](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a>CDBException::m_nRetCode

Contient un code d’erreur ODBC de type RETCODE retourné par une fonction d’interface de programmation d’applications ODBC (API).

### <a name="remarks"></a>Notes

Ce type comprend les codes préfixés SQL définis par ODBC et les codes préfixés AFX_SQL définis par les classes de base de données. Pour `CDBException`un , ce membre contiendra l’une des valeurs suivantes :

- AFX_SQL_ERROR_API_CONFORMANCE Le conducteur d’un `CDatabase::Open` ou d’un `CDatabase::OpenEx` appel n’est pas conforme au niveau 1 (SQL_OAC_LEVEL1) requis pour l’ODBC API Conformance ( SQL_OAC_LEVEL1).

- AFX_SQL_ERROR_CONNECT_FAIL Connexion à la source de données a échoué. Vous avez`CDatabase` passé un pointeur NULL à votre constructeur de `GetDefaultConnect` recordset et la tentative ultérieure de créer une connexion basée sur échoué.

- AFX_SQL_ERROR_DATA_TRUNCATED Vous avez demandé plus de données que vous n’en avez fourni le stockage. Pour obtenir de l’information `CString` `CByteArray` sur l’augmentation `nMaxLength` du stockage des données ou des types de données fournis, consultez l’argument [de RFX_Text](record-field-exchange-functions.md#rfx_text) et [RFX_Binary](record-field-exchange-functions.md#rfx_binary) sous « Macros and Globals ».

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED Un appel à `CRecordset::Open` la demande d’un dynaset a échoué. Les dynasets ne sont pas pris en charge par le conducteur.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST Vous avez tenté d’ouvrir une table (ou ce que vous avez donné n’a pas pu être identifié comme un appel `DoFieldExchange` de procédure ou une déclaration **SELECT),** mais il n’y a pas de colonnes identifiées dans les appels de fonction d’échange de champ record (RFX) dans votre remplacement.

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH Le type de fonction RFX `DoFieldExchange` dans votre remplacement n’est pas compatible avec le type de données de colonne dans le jeu d’enregistrement.

- AFX_SQL_ERROR_ILLEGAL_MODE Vous avez `CRecordset::Update` appelé sans `CRecordset::AddNew` `CRecordset::Edit`appeler auparavant ou .

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED Votre demande de verrouillage des dossiers de mise à jour n’a pas pu être remplie parce que votre pilote ODBC ne prend pas en charge le verrouillage.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED Vous avez `CRecordset::Update` appelé `Delete` ou pour une table sans clé unique et changé plusieurs enregistrements.

- AFX_SQL_ERROR_NO_CURRENT_RECORD Vous avez tenté de modifier ou de supprimer un enregistrement précédemment supprimé. Vous devez faire défiler vers un nouvel enregistrement en cours après une suppression.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES Votre demande de dynaset n’a pas pu être satisfaite parce que votre pilote ODBC ne prend pas en charge les mises à jour positionnées.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED Vous avez `CRecordset::Update` appelé `Delete`ou , mais quand l’opération a commencé le dossier ne pouvait plus être trouvé.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED Une tentative de charger l’ODBC. DLL a échoué; Windows ne pouvait pas trouver ou ne pouvait pas charger ce DLL. Cette erreur est fatale.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED Votre demande de dynaset n’a pas pu être satisfaite parce qu’un pilote ODBC conforme au niveau 2 est nécessaire.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY Une tentative de faire défiler n’a pas réussi parce que la source de données ne prend pas en charge le défilement vers l’arrière.

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED Un appel à `CRecordset::Open` la demande d’un instantané a échoué. Les instantanés ne sont pas pris en charge par le conducteur. (Cela ne devrait se produire que lorsque la bibliothèque de curseurs ODBC ODBCCURS. DLL n’est pas présent.)

- AFX_SQL_ERROR_SQL_CONFORMANCE Le conducteur d’un `CDatabase::Open` appel ou d’un `CDatabase::OpenEx` appel n’est pas conforme au niveau de conformité ODBC SQL requis de «minimum» (SQL_OSC_MINIMUM).

- AFX_SQL_ERROR_SQL_NO_TOTAL Le conducteur de l’ODBC n’a `CLongBinary` pas été en mesure de préciser la taille totale d’une valeur de données. L’opération a probablement échoué parce qu’un bloc de mémoire global ne pouvait pas être préaffecté.

- AFX_SQL_ERROR_RECORDSET_READONLY Vous avez tenté de mettre à jour un jeu d’enregistrement de lecture seulement, ou la source de données est lue uniquement. Aucune opération de mise à jour `CDatabase` ne peut être effectuée avec l’ensemble d’enregistrements ou l’objet à qui il est associé.

- SQL_ERROR fonction a échoué. Le message d’erreur retourné `SQLError` par la `m_strError` fonction ODBC est stocké dans le membre des données.

- SQL_INVALID_HANDLE fonction a échoué en raison d’une poignée d’environnement invalide, poignée de connexion, ou poignée de déclaration. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible `SQLError`à partir de la fonction ODBC .

Les codes préfixés SQL sont définis par ODBC. Les codes préfixés AFX sont définis dans AFXDB. H, trouvé dans MFC-INCLUDE.

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a>CDBException::m_strError

Contient une chaîne décrivant l’erreur qui a causé l’exception.

### <a name="remarks"></a>Notes

La chaîne décrit l’erreur en termes alphanumériques. Pour plus d’informations détaillées `m_strStateNativeOrigin`et un exemple, voir .

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a>CDBException::m_strStateNativeOrigin

Contient une chaîne décrivant l’erreur qui a causé l’exception.

### <a name="remarks"></a>Notes

La chaîne est de la forme "Etat:%s,Native:%ld,Origin:%s", où les codes de format, dans l’ordre, sont remplacés par des valeurs qui décrivent:

- Le SQLSTATE, une chaîne à durée nulle contenant un code d’erreur de cinq caractères `SQLError`retourné dans le paramètre *szSqlState* de la fonction ODBC . Les valeurs SQLSTATE sont répertoriées à l’Annexe A, [ODBC Error Codes](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes), dans la *référence du programmeur ODBC*. Exemple : « S0022 ».

- Le code d’erreur natif, spécifique à la source de données, `SQLError` est retourné dans le paramètre *pfNativeError* de la fonction. Exemple : 207.

- Le texte du message d’erreur est retourné dans `SQLError` le paramètre *szErrorMsg* de la fonction. Ce message se compose de plusieurs noms entre crochets. Comme une erreur est transmise de sa source à l’utilisateur, chaque composant ODBC (source de données, pilote, Driver Manager) joint son propre nom. Ces informations permettent de déterminer l’origine de l’erreur. Exemple : [Microsoft][ODBC SQL Server Driver][SQL Server]

Le cadre interprète la chaîne d’erreur `m_strStateNativeOrigin`et met ses composants dans ; si `m_strStateNativeOrigin` contient des informations pour plus d’une erreur, les erreurs sont séparées par des lignes neuves. Le cadre met le texte d’erreur alphanumérique dans `m_strError`.

Pour plus d’informations sur les codes utilisés pour constituer cette chaîne, consultez la fonction [SQLError](/sql/odbc/reference/syntax/sqlerror-function) dans la *référence du programmeur ODBC*.

### <a name="example"></a>Exemple

De ODBC:\["State:S0022,Native:207,Origin:\[Microsoft] ODBC\[SQL Server Driver] SQL Server] Invalid column name 'ColName'"

Dans `m_strStateNativeOrigin`:\["State:S0022,Native:207,Origin:\[Microsoft] ODBC\[SQL Server Driver] SQL Server]"

Dans `m_strError`: "Nom de colonne invalide 'ColName'"

## <a name="see-also"></a>Voir aussi

[Classe CException](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Classe CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Mise à jour](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Déléte](../../mfc/reference/crecordset-class.md#delete)<br/>
[Classe CException](../../mfc/reference/cexception-class.md)
