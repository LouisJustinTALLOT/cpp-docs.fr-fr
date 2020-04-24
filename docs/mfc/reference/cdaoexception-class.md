---
title: Classe CDaoException
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
ms.openlocfilehash: 935d7870d68554d702e2ad762e83343cb518b2b8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754726"
---
# <a name="cdaoexception-class"></a>Classe CDaoException

Représente une condition d'exception résultant des classes de base de données MFC basées sur des objets d'accès aux données (DAO). DAO 3.6 est la version finale, et il est considéré comme obsolète.

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
|[CDaoException::GetErrorInfo](#geterrorinfo)|Renvoie des informations d’erreur sur un objet d’erreur particulier dans la collection d’erreurs.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Contient un code d’erreur étendu pour toute erreur dans les classes MFC DAO.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Un pointeur vers un objet [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) qui contient des informations sur un objet d’erreur DAO.|
|[CDaoException::m_scode](#m_scode)|La valeur [SCODE](#m_scode) associée à l’erreur.|

## <a name="remarks"></a>Notes

Le cours comprend les membres des données publiques que vous pouvez utiliser pour déterminer la cause de l’exception. `CDaoException`les objets sont construits et jetés par les fonctions des membres des classes de base de données DAO.

> [!NOTE]
> Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur la connectivité open Database (ODBC). Tous les noms de classe de base de données DAO ont le préfixe "CDao". Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus capables que les classes MFC basées sur ODBC; les classes basées sur le DAO peuvent accéder aux données, y compris par l’intermédiaire des pilotes ODBC, via leur propre moteur de base de données. Les classes basées sur le DAO prennent également en charge les opérations de langage de définition des données (DDL), telles que l’ajout de tables via les classes, sans avoir à appeler directement DAO. Pour plus d’informations sur les exceptions lancées par les classes ODBC, voir [CDBException](../../mfc/reference/cdbexception-class.md).

Vous pouvez accéder à des objets d’exception dans le cadre d’une expression [CATCH.](../../mfc/reference/exception-processing.md#catch) Vous pouvez `CDaoException` également jeter des objets de votre propre code avec la fonction globale [AfxThrowDaoException.](../../mfc/reference/exception-processing.md#afxthrowdaoexception)

Dans MFC, toutes les erreurs DAO `CDaoException`sont exprimées comme des exceptions, de type . Lorsque vous attrapez une exception de `CDaoException` ce type, vous pouvez utiliser les fonctions des membres pour récupérer les informations de tous les objets d’erreur DAO stockés dans la collection d’erreurs du moteur de base de données. Au fur et à mesure que chaque erreur se produit, un ou plusieurs objets d’erreur sont placés dans la collection d’erreurs. (Normalement, la collection ne contient qu’un seul objet d’erreur; si vous utilisez une source de données ODBC, vous êtes plus susceptible d’obtenir plusieurs objets d’erreur.) Lorsqu’une autre opération DAO génère une erreur, la collection d’erreurs est effacée et le nouvel objet d’erreur est placé dans la collection d’erreurs. Les opérations DAO qui ne génèrent pas d’erreur n’ont aucun effet sur la collecte d’erreurs.

Pour les codes d’erreur DAO, voir le fichier DAOERR. H. Pour plus d’informations, consultez le thème « Erreurs d’accès aux données trappables » dans DAO Help.

Pour plus d’informations sur le `CDaoException` traitement des exceptions en général, ou sur les objets, voir les articles [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md) et [Exceptions: Database Exceptions](../../mfc/exceptions-database-exceptions.md). Le deuxième article contient un exemple de code qui illustre la gestion des exceptions dans DAO.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>CDaoException::CDaoException

Construit un objet `CDaoException`.

```
CDaoException();
```

### <a name="remarks"></a>Notes

Normalement, le cadre crée des objets d’exception lorsque son code lance une exception. Vous avez rarement besoin de construire un objet d’exception explicitement. Si vous voulez `CDaoException` jeter un de votre propre code, appelez la fonction globale [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Cependant, vous pouvez créer explicitement un objet d’exception si vous faites des appels directs vers DAO via les indications d’interface DAO que les classes MFC encapsulent. Dans ce cas, vous devrez peut-être récupérer des informations d’erreur de DAO. Supposons qu’une erreur se produise dans DAO lorsque vous appelez une méthode DAO via l’interface DAODatabases à la collection de bases de données d’un espace de travail.

##### <a name="to-retrieve-the-dao-error-information"></a>Pour récupérer les informations d’erreur DAO

1. Construire `CDaoException` un objet.

1. Appelez la fonction de membre [GetErrorCount](#geterrorcount) de l’objet d’exception pour déterminer le nombre d’objets d’erreur dans la collection d’erreurs du moteur de base de données. (Normalement, un seul, sauf si vous utilisez une source de données ODBC.)

1. Appelez la fonction de membre [GetErrorInfo](#geterrorinfo) de l’objet d’exception pour récupérer un objet d’erreur spécifique à la fois, par index dans la collection, via l’objet d’exception. Considérez l’objet d’exception comme un proxy pour un objet d’erreur DAO.

1. Examinez la structure [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) actuelle qui `GetErrorInfo` revient dans le [m_pErrorInfo](#m_perrorinfo) membre des données. Ses membres fournissent des informations sur l’erreur du DAO.

1. Dans le cas d’une source de données ODBC, répétez les étapes 3 et 4 au besoin, pour plus d’objets d’erreur.

1. Si vous avez construit l’objet d’exception sur le tas, supprimez-le avec l’opérateur **de suppression** lorsque vous avez terminé.

Pour plus d’informations sur le traitement des erreurs dans les classes MFC DAO, voir l’article [Exceptions: Database Exceptions](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>CDaoException::GetErrorCount

Appelez cette fonction de membre pour récupérer le nombre d’objets d’erreur DAO dans la collection Erreurs du moteur de base de données.

```
short GetErrorCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’objets d’erreur DAO dans la collection Erreurs du moteur de base de données.

### <a name="remarks"></a>Notes

Ces informations sont utiles pour boucler la collection d’erreurs pour récupérer chacun des un ou plusieurs objets d’erreur DAO de la collection. Pour récupérer un objet d’erreur par index ou par numéro d’erreur DAO, appelez la fonction membre [GetErrorInfo.](#geterrorinfo)

> [!NOTE]
> Normalement, il n’y a qu’un seul objet d’erreur dans la collection d’erreurs. Toutefois, si vous travaillez avec une source de données ODBC, il pourrait y en avoir plus d’un.

## <a name="cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>CDaoException::GetErrorInfo

Renvoie des informations d’erreur sur un objet d’erreur particulier dans la collection d’erreurs.

```cpp
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index des informations d’erreur dans la collection d’erreurs du moteur de base de données, pour le lookup par index.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour obtenir les types suivants d’information sur l’exception :

- Code d'erreur

- Source

- Description

- Fichier d'aide

- Contexte d’aide

`GetErrorInfo`stocke les informations dans `m_pErrorInfo` le membre des données de l’objet d’exception. Pour une brève description de l’information retournée, voir [m_pErrorInfo](#m_perrorinfo). Si vous attrapez `CDaoException` une exception de `m_pErrorInfo` type lancée par MFC, le membre sera déjà rempli. Si vous choisissez d’appeler DAO directement, vous `GetErrorInfo` devez appeler `m_pErrorInfo`la fonction de membre de l’objet d’exception vous-même pour remplir . Pour une description plus détaillée, consultez la structure [CDaoErrorInfo.](../../mfc/reference/cdaoerrorinfo-structure.md)

Pour plus d’informations sur les exceptions DAO, et le code exemple, voir l’article [Exceptions: Bases de données Exceptions](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptionm_nafxdaoerror"></a><a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError

Contient un code d’erreur étendu MFC.

### <a name="remarks"></a>Notes

Ce code est fourni dans les cas où un composant spécifique des classes MFC DAO a commis une erreur.

Les valeurs possibles sont les suivantes :

- NO_AFX_DAO_ERROR L’opération la plus récente n’a pas entraîné une erreur prolongée de MFC. Cependant, l’opération aurait pu produire d’autres erreurs de DAO ou OLE, de sorte que vous devriez vérifier [m_pErrorInfo](#m_perrorinfo) et peut-être [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC n’a pas pu initialiser le moteur de base de données Microsoft Jet. OLE n’a peut-être pas été parasémis, ou il aurait pu être impossible de créer une instance de l’objet moteur de base de données DAO. Ces problèmes suggèrent généralement une mauvaise installation de DAO ou OLE.

- AFX_DAO_ERROR_DFX_BIND Une adresse utilisée dans un appel de fonction d’échange de dossiers DAO (DFX) n’existe pas ou est invalide (l’adresse n’a pas été utilisée pour lier les données). Vous avez peut-être passé une mauvaise adresse dans un appel DFX, ou l’adresse pourrait être devenue invalide entre les opérations DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN Vous avez tenté d’ouvrir un ensemble d’enregistrements basé sur une requête ou un objet de dépôt qui n’était pas à l’état d’ouverture.

## <a name="cdaoexceptionm_perrorinfo"></a><a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo

Contient un pointeur vers une `CDaoErrorInfo` structure qui fournit des informations sur l’objet d’erreur DAO que vous avez récupéré pour la dernière fois en appelant [GetErrorInfo](#geterrorinfo).

### <a name="remarks"></a>Notes

Cet objet contient les informations suivantes :

|Membre de CDaoErrorInfo|Information|Signification|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Code d'erreur|Le code d’erreur DAO|
|`m_strSource`|Source|Le nom de l’objet ou de l’application qui a généré à l’origine l’erreur|
|`m_strDescription`|Description|Une chaîne descriptive associée à l’erreur|
|`m_strHelpFile`|Fichier d’aide|Un chemin vers un fichier d’aide Windows dans lequel l’utilisateur peut obtenir des informations sur le problème|
|`m_lHelpContext`|Contexte d’aide|L’ID context pour un sujet dans le fichier DAO Help|

Pour plus de détails sur `CDaoErrorInfo` les informations contenues dans l’objet, consultez la structure [CDaoErrorInfo.](../../mfc/reference/cdaoerrorinfo-structure.md)

## <a name="cdaoexceptionm_scode"></a><a name="m_scode"></a>CDaoException::m_scode

Contient une valeur `SCODE` de type qui décrit l’erreur.

### <a name="remarks"></a>Notes

Il s’agit d’un code OLE. Vous aurez rarement besoin d’utiliser cette valeur parce que, dans presque tous les `CDaoException` cas, des informations plus spécifiques sur les erreurs de MFC ou DAO sont disponibles dans les autres membres de données.

Pour plus d’informations sur SCODE, consultez le thème [Structure des codes d’erreur OLE](/windows/win32/com/structure-of-com-error-codes) dans le SDK Windows. Les cartes de type de données SCODE au type de données HRESULT.

## <a name="see-also"></a>Voir aussi

[Classe CException](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CException](../../mfc/reference/cexception-class.md)
