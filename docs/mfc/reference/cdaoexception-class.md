---
title: CDaoException (classe)
ms.date: 09/17/2019
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: 262c9b75771611dc04938fa5d9f58c3f7e5fc2ef
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096130"
---
# <a name="cdaoexception-class"></a>CDaoException (classe)

Représente une condition d'exception résultant des classes de base de données MFC basées sur des objets d'accès aux données (DAO).
DAO 3,6 est la version finale et est considérée comme obsolète.

## <a name="syntax"></a>Syntaxe

```
class CDaoException : public CException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|Construit un objet `CDaoException`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|Retourne le nombre d’erreurs dans la collection d’erreurs du moteur de base de données.|
|[CDaoException::GetErrorInfo](#geterrorinfo)|Retourne des informations d’erreur sur un objet d’erreur particulier dans la collection d’erreurs.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Contient un code d’erreur étendu pour toute erreur dans les classes DAO MFC.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Pointeur vers un objet [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) qui contient des informations sur un objet d’erreur DAO.|
|[CDaoException::m_scode](#m_scode)|Valeur [SCODE](#m_scode) associée à l’erreur.|

## <a name="remarks"></a>Notes

La classe comprend des membres de données publics que vous pouvez utiliser pour déterminer la cause de l’exception. `CDaoException`les objets sont construits et levés par les fonctions membres des classes de base de données DAO.

> [!NOTE]
>  Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur Open Database Connectivity (ODBC). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus puissantes que les classes MFC basées sur ODBC ; les classes basées sur DAO peuvent accéder aux données, notamment via des pilotes ODBC, via leur propre moteur de base de données. Les classes basées sur DAO prennent également en charge les opérations de langage de définition de données (DDL, Data Definition Language), telles que l’ajout de tables via les classes, sans avoir à appeler DAO directement. Pour plus d’informations sur les exceptions levées par les classes ODBC, consultez [CDBException](../../mfc/reference/cdbexception-class.md).

Vous pouvez accéder aux objets d’exception dans la portée d’une expression [catch](../../mfc/reference/exception-processing.md#catch) . Vous pouvez également lever `CDaoException` des objets à partir de votre propre code avec la fonction globale [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) .

Dans MFC, toutes les erreurs DAO sont exprimées en tant qu' `CDaoException`exceptions, de type. Quand vous interceptez une exception de ce type, vous pouvez `CDaoException` utiliser des fonctions membres pour récupérer des informations à partir de n’importe quel objet d’erreur DAO stocké dans la collection d’erreurs du moteur de base de données. À mesure que chaque erreur se produit, un ou plusieurs objets Error sont placés dans la collection Errors. (Normalement, la collection contient un seul objet d’erreur ; si vous utilisez une source de données ODBC, vous risquez d’obtenir plusieurs objets d’erreur.) Lorsqu’une autre opération DAO génère une erreur, la collection Errors est désactivée et le nouvel objet Error est placé dans la collection Errors. Les opérations DAO qui ne génèrent pas d’erreur n’ont aucun effet sur la collection Errors.

Pour les codes d’erreur DAO, consultez le fichier DAOERR. Manutention. Pour obtenir des informations connexes, consultez la rubrique « Erreurs d’accès aux données récupérables » dans l’aide de DAO.

Pour plus d’informations sur la gestion des exceptions en général `CDaoException` , ou sur les objets, consultez les articles sur la [ [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md) et les exceptions : Exceptions](../../mfc/exceptions-database-exceptions.md)de base de données. Le deuxième article contient un exemple de code qui illustre la gestion des exceptions dans DAO.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

##  <a name="cdaoexception"></a>  CDaoException::CDaoException

Construit un objet `CDaoException`.

```
CDaoException();
```

### <a name="remarks"></a>Notes

En règle générale, l’infrastructure crée des objets exception lorsque son code lève une exception. Vous devez rarement construire un objet exception explicitement. Si vous souhaitez lever une `CDaoException` à partir de votre propre code, appelez la fonction globale [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Toutefois, vous souhaiterez peut-être créer explicitement un objet exception si vous effectuez des appels directs à DAO via les pointeurs d’interface DAO que les classes MFC encapsulent. Dans ce cas, vous devrez peut-être récupérer les informations d’erreur à partir de DAO. Supposons qu’une erreur se produit dans DAO lorsque vous appelez une méthode DAO par le biais de l’interface DAODatabases à la collection de bases de données d’un espace de travail.

##### <a name="to-retrieve-the-dao-error-information"></a>Pour récupérer les informations sur l’erreur DAO

1. Construisez `CDaoException` un objet.

1. Appelez la fonction membre [GetErrorCount](#geterrorcount) de l’objet exception pour déterminer le nombre d’objets Error présents dans la collection d’erreurs du moteur de base de données. (En général, un seul, sauf si vous utilisez une source de données ODBC.)

1. Appelez la fonction membre [GetErrorInfo](#geterrorinfo) de l’objet exception pour récupérer un objet d’erreur spécifique à la fois, par index dans la collection, par le biais de l’objet exception. Considérez l’objet exception comme un proxy pour un objet d’erreur DAO.

1. Examinez la structure [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) actuelle `GetErrorInfo` qui retourne le membre de données [m_pErrorInfo](#m_perrorinfo) . Ses membres fournissent des informations sur l’erreur DAO.

1. Dans le cas d’une source de données ODBC, répétez les étapes 3 et 4, si nécessaire, pour d’autres objets d’erreur.

1. Si vous avez construit l’objet exception sur le tas, supprimez-le à l’aide de l’opérateur **Delete** lorsque vous avez terminé.

Pour plus d’informations sur la gestion des erreurs dans les classes DAO MFC, [consultez l’article exceptions : Exceptions](../../mfc/exceptions-database-exceptions.md)de base de données.

##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount

Appelez cette fonction membre pour récupérer le nombre d’objets d’erreur DAO dans la collection d’erreurs du moteur de base de données.

```
short GetErrorCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’objets d’erreur DAO dans la collection d’erreurs du moteur de base de données.

### <a name="remarks"></a>Notes

Ces informations sont utiles pour effectuer une boucle dans la collection Errors afin de récupérer chacun des objets d’erreur DAO dans la collection. Pour récupérer un objet d’erreur par index ou par numéro d’erreur DAO, appelez la fonction membre [GetErrorInfo](#geterrorinfo) .

> [!NOTE]
>  Normalement, la collection Errors ne contient qu’un seul objet Error. Toutefois, si vous utilisez une source de données ODBC, il peut y en avoir plusieurs.

##  <a name="geterrorinfo"></a>  CDaoException::GetErrorInfo

Retourne des informations d’erreur sur un objet d’erreur particulier dans la collection d’erreurs.

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index des informations d’erreur dans la collection d’erreurs du moteur de base de données, pour la recherche par index.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour obtenir les genres d’informations suivants à propos de l’exception :

- Code d'erreur

- source

- Description

- Fichier d'aide

- Contexte d’aide

`GetErrorInfo`stocke les informations dans le membre de `m_pErrorInfo` données de l’objet exception. Pour obtenir une brève description des informations retournées, consultez [m_pErrorInfo](#m_perrorinfo). Si vous interceptez une exception de `CDaoException` type levée par MFC, `m_pErrorInfo` le membre sera déjà rempli. Si vous choisissez d’appeler DAO directement, vous devez appeler la fonction membre de `GetErrorInfo` l’objet exception vous- `m_pErrorInfo`même pour remplir. Pour obtenir une description plus détaillée, consultez la structure [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) .

Pour plus d’informations sur les exceptions DAO et l’exemple de code [, consultez l’article exceptions : Exceptions](../../mfc/exceptions-database-exceptions.md)de base de données.

##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError

Contient un code d’erreur étendu MFC.

### <a name="remarks"></a>Notes

Ce code est fourni dans les cas où un composant spécifique des classes DAO MFC s’est commis.

Les valeurs possibles sont les suivantes :

- NO_AFX_DAO_ERROR l’opération la plus récente n’a pas abouti à une erreur étendue MFC. Toutefois, l’opération peut avoir produit d’autres erreurs à partir de DAO ou OLE, donc vous devez vérifier [m_pErrorInfo](#m_perrorinfo) et éventuellement [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC n’a pas pu initialiser le moteur de base de données Microsoft Jet. OLE n’a peut-être pas pu s’initialiser, ou il est impossible de créer une instance de l’objet du moteur de base de données DAO. Ces problèmes suggèrent généralement une installation incorrecte de DAO ou OLE.

- AFX_DAO_ERROR_DFX_BIND une adresse utilisée dans un appel de fonction d’échange de champs d’enregistrements DAO (DFX) n’existe pas ou n’est pas valide (l’adresse n’a pas été utilisée pour lier des données). Vous avez peut-être passé une mauvaise adresse dans un appel DFX ou l’adresse n’est peut-être plus valide entre les opérations DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN vous avez tenté d’ouvrir un jeu d’enregistrements basé sur un objet querydef ou TableDef qui n’était pas dans un état ouvert.

##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo

Contient un pointeur vers une `CDaoErrorInfo` structure qui fournit des informations sur l’objet d’erreur DAO que vous avez récupéré en dernier en appelant [GetErrorInfo](#geterrorinfo).

### <a name="remarks"></a>Notes

Cet objet contient les informations suivantes :

|Membre CDaoErrorInfo|Information|Signification|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Code d'erreur|Code d’erreur DAO|
|`m_strSource`|source|Nom de l’objet ou de l’application qui a généré l’erreur à l’origine|
|`m_strDescription`|Description|Chaîne descriptive associée à l’erreur.|
|`m_strHelpFile`|Fichier d’aide|Chemin d’accès à un fichier d’aide Windows dans lequel l’utilisateur peut obtenir des informations sur le problème|
|`m_lHelpContext`|Contexte d’aide|ID de contexte pour une rubrique dans le fichier d’aide DAO|

Pour obtenir des informations complètes sur les informations contenues dans l' `CDaoErrorInfo` objet, consultez la structure [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) .

##  <a name="m_scode"></a>  CDaoException::m_scode

Contient une valeur de type `SCODE` qui décrit l’erreur.

### <a name="remarks"></a>Notes

Il s’agit d’un code OLE. Vous devrez rarement utiliser cette valeur car, dans presque tous les cas, des informations d’erreur MFC ou DAO spécifiques sont disponibles dans les autres `CDaoException` membres de données.

Pour plus d’informations sur SCODE, consultez la rubrique [structure des codes d’erreur OLE](/windows/win32/com/structure-of-com-error-codes) dans le SDK Windows. Le type de données SCODE est mappé au type de données HRESULT.

## <a name="see-also"></a>Voir aussi

[CException, classe](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CException, classe](../../mfc/reference/cexception-class.md)
