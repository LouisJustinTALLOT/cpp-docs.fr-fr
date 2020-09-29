---
title: CDynamicParameterAccessor (classe)
ms.date: 02/14/2018
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
- ATL::CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor.GetParamCount
- GetParamCount
- ATL.CDynamicParameterAccessor.GetParamCount
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
helpviewer_keywords:
- CDynamicParameterAccessor class
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
- GetParam method
- GetParamCount method
- GetParamIO method
- GetParamLength method
- GetParamName method
- GetParamStatus method
- GetParamString method
- GetParamType method
- SetParam method
- SetParamLength method
- SetParamStatus method
- SetParamString method
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
ms.openlocfilehash: 4596f5181dd197b16786ee4d4d16cf06721b13b6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498657"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor (classe)

Semblable à [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) mais obtient les informations sur les paramètres à définir en appelant l’interface [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) .

## <a name="syntax"></a>Syntax

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>Configuration requise

**En-tête**: atldbcli. h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|Constructeur.|
|[GetParam](#getparam)|Récupère les données du paramètre en mémoire tampon.|
|[GetParamCount](#getparamcount)|Récupère le nombre de paramètres dans l’accesseur.|
|[GetParamIO](#getparamio)|Détermine si le paramètre spécifié est un paramètre d’entrée ou de sortie.|
|[GetParamLength](#getparamlength)|Récupère la longueur du paramètre spécifié stocké en mémoire tampon.|
|[GetParamName](#getparamname)|Récupère le nom d’un paramètre spécifique.|
|[GetParamStatus](#getparamstatus)|Récupère l’état du paramètre spécifié stocké en mémoire tampon.|
|[GetParamString](#getparamstring)|Récupère les données de chaîne du paramètre spécifié stocké en mémoire tampon.|
|[GetParamType](#getparamtype)|Récupère le type de données d’un paramètre spécifique.|
|[SetParam](#setparam)|Définit la mémoire tampon à l’aide des données de paramètre.|
|[SetParamLength](#setparamlength)|Définit la longueur du paramètre spécifié stocké en mémoire tampon.|
|[SetParamStatus](#setparamstatus)|Définit l’état du paramètre spécifié stocké en mémoire tampon.|
|[SetParamString](#setparamstring)|Définit les données de chaîne du paramètre spécifié stocké en mémoire tampon.|

## <a name="remarks"></a>Remarques

Le fournisseur doit prendre en charge `ICommandWithParameters` pour permettre au consommateur d’utiliser cette classe.

Les informations sur les paramètres sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenez les données de paramètre à partir de la mémoire tampon via [GetParam](#getparam) et [GetParamType](#getparamtype).

Pour obtenir un exemple montrant comment utiliser cette classe pour exécuter une SQL Server procédure stockée et obtenir les valeurs de paramètre de sortie, consultez l’exemple de code [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) dans le référentiel [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) sur GitHub.

## <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a><a name="cdynamicparameteraccessor"></a> CDynamicParameterAccessor :: CDynamicParameterAccessor

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
typedef CDynamicParameterAccessor _ParamClass;
CDynamicParameterAccessor(
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000 )
   : CDynamicAccessor(eBlobHandling, nBlobSize )
```

#### <a name="parameters"></a>Paramètres

*eBlobHandling*<br/>
Spécifie comment les données d’objet BLOB doivent être gérées. La valeur par défaut est DBBLOBHANDLING_DEFAULT. Pour obtenir une description des valeurs DBBLOBHANDLINGENUM, consultez [CDynamicAccessor :: SetBlobHandling](./cdynamicaccessor-class.md#setblobhandling) .

*nBlobSize*<br/>
Taille maximale d’objet BLOB en octets ; les données de colonne sur cette valeur sont traitées comme un objet BLOB. La valeur par défaut est 8 000. Pour plus d’informations, consultez [CDynamicAccessor :: SetBlobSizeLimit](./cdynamicaccessor-class.md#setblobsizelimit) .

### <a name="remarks"></a>Remarques

Pour plus d’informations sur la gestion des objets BLOB, consultez le constructeur [CDynamicAccessor :: CDynamicAccessor](./cdynamicaccessor-class.md#cdynamicaccessor) .

## <a name="cdynamicparameteraccessorgetparam"></a><a name="getparam"></a> CDynamicParameterAccessor :: GetParam

Récupère les données qui ne sont pas de type chaîne pour un paramètre spécifié à partir de la mémoire tampon de paramètres.

### <a name="syntax"></a>Syntaxe

```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,
   ctype* pData) const throw();

template <class ctype> bool GetParam(TCHAR* pParamName,
   ctype* pData) const throw();

void* GetParam(DBORDINAL nParam) const throw();

void* GetParam(TCHAR* pParamName) const throw();
```

#### <a name="parameters"></a>Paramètres

*ctype*<br/>
Paramètre basé sur un modèle qui est le type de données.

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*pParamName*<br/>
dans Nom du paramètre.

*pData*<br/>
à Pointeur vers la mémoire qui contient les données récupérées de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Pour les versions sans modèle, pointe vers la mémoire qui contient les données récupérées à partir de la mémoire tampon. Pour les versions basées sur un modèle, retourne **`true`** en cas de réussite ou **`false`** en cas d’échec.

Utilisez `GetParam` pour récupérer des données de paramètre sans chaîne à partir de la mémoire tampon. Utilisez [GetParamString](#getparamstring) pour récupérer des données de paramètre de chaîne à partir de la mémoire tampon.

## <a name="cdynamicparameteraccessorgetparamcount"></a><a name="getparamcount"></a> CDynamicParameterAccessor :: GetParamCount

Récupère le nombre de paramètres stockés dans la mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de paramètres.

## <a name="cdynamicparameteraccessorgetparamio"></a><a name="getparamio"></a> CDynamicParameterAccessor :: GetParamIO

Détermine si le paramètre spécifié est un paramètre d’entrée ou de sortie.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*pParamIO*<br/>
Pointeur vers la variable contenant le `DBPARAMIO` type (entrée ou sortie) du paramètre spécifié. La définition est la suivante :

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** en cas de réussite ou **`false`** d’échec.

## <a name="cdynamicparameteraccessorgetparamlength"></a><a name="getparamlength"></a> CDynamicParameterAccessor :: GetParamLength

Récupère la longueur du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*pLength*<br/>
à Pointeur vers la variable contenant la longueur en octets du paramètre spécifié.

### <a name="remarks"></a>Remarques

La première substitution retourne **`true`** en cas de réussite ou **`false`** d’échec. Le deuxième remplacement pointe vers la mémoire qui contient la longueur du paramètre.

## <a name="cdynamicparameteraccessorgetparamname"></a><a name="getparamname"></a> CDynamicParameterAccessor :: GetParamName

Récupère le nom du paramètre spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

### <a name="return-value"></a>Valeur renvoyée

Nom du paramètre spécifié.

## <a name="cdynamicparameteraccessorgetparamstatus"></a><a name="getparamstatus"></a> CDynamicParameterAccessor :: GetParamStatus

Récupère l’état du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*pStatus*<br/>
à Pointeur vers la variable qui contient l’État DBSTATUS du paramètre spécifié. Pour plus d’informations sur les valeurs de DBSTATUS, consultez l' [État](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*ou recherchez DBSTATUS dans OleDb. h.

### <a name="remarks"></a>Remarques

La première substitution retourne **`true`** en cas de réussite ou **`false`** d’échec. Le deuxième remplacement pointe vers la mémoire qui contient l’état du paramètre spécifié.

## <a name="cdynamicparameteraccessorgetparamstring"></a><a name="getparamstring"></a> CDynamicParameterAccessor :: GetParamString

Récupère les données de chaîne du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamString(DBORDINAL nParam,
   CSimpleStringA& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CSimpleStringW& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CHAR* pBuffer,
   size_t* pMaxLen) throw();

bool GetParamString(DBORDINAL nParam,
   WCHAR* pBuffer,
   size_t* pMaxLen) throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*strOutput*<br/>
à `CSimpleStringA`Données de chaîne ANSI () ou Unicode ( `CSimpleStringW` ) du paramètre spécifié. Vous devez passer un paramètre de type `CString` , par exemple :

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
à Pointeur vers les données de chaîne ANSI (**char**) ou Unicode (**WCHAR**) du paramètre spécifié.

*pMaxLen*<br/>
à Pointeur vers la taille de la mémoire tampon vers laquelle pointe *pbuffer* (en caractères, y compris le caractère null de fin).

### <a name="remarks"></a>Remarques

Retourne **`true`** en cas de réussite ou **`false`** d’échec.

Si *pbuffer* a la valeur null, cette méthode définit la taille de mémoire tampon requise dans la mémoire vers laquelle pointe *pMaxLen* et retourne **`true`** sans copier les données.

Cette méthode échoue si le *pbuffer* de mémoire tampon n’est pas assez grand pour contenir la chaîne entière.

Utilisez `GetParamString` pour récupérer des données de paramètre de chaîne à partir de la mémoire tampon. Utilisez [GetParam](#getparam) pour récupérer des données de paramètre sans chaîne à partir de la mémoire tampon.

## <a name="cdynamicparameteraccessorgetparamtype"></a><a name="getparamtype"></a> CDynamicParameterAccessor :: GetParamType

Récupère le type de données d’un paramètre spécifique.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*pType*<br/>
à Pointeur vers la variable contenant le type de données du paramètre spécifié.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** en cas de réussite ou **`false`** d’échec.

## <a name="cdynamicparameteraccessorsetparam"></a><a name="setparam"></a> CDynamicParameterAccessor :: SetParam

Définit la mémoire tampon des paramètres à l’aide des données (non-chaîne) spécifiées.

### <a name="syntax"></a>Syntaxe

```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,
   constctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();

template <class ctype>
bool SetParam(TCHAR* pParamName,
   const ctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>Paramètres

*ctype*<br/>
Paramètre basé sur un modèle qui est le type de données.

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Par exemple :

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pParamName*<br/>
dans Nom du paramètre.

*pData*<br/>
dans Pointeur vers la mémoire qui contient les données à écrire dans la mémoire tampon.

*statut*<br/>
dans État de la colonne DBSTATUS. Pour plus d’informations sur les valeurs de DBSTATUS, consultez l' [État](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*ou recherchez DBSTATUS dans OleDb. h.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** en cas de réussite ou **`false`** d’échec.

Utilisez `SetParam` pour définir des données de paramètre sans chaîne dans la mémoire tampon. Utilisez [SetParamString](#setparamstring) pour définir les données de paramètre de chaîne dans la mémoire tampon.

## <a name="cdynamicparameteraccessorsetparamlength"></a><a name="setparamlength"></a> CDynamicParameterAccessor :: SetParamLength

Définit la longueur du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*length*<br/>
dans Longueur, en octets, du paramètre spécifié.

### <a name="remarks"></a>Remarques

Retourne **`true`** en cas de réussite ou **`false`** d’échec.

## <a name="cdynamicparameteraccessorsetparamstatus"></a><a name="setparamstatus"></a> CDynamicParameterAccessor :: SetParamStatus

Définit l’état du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*statut*<br/>
dans État DBSTATUS du paramètre spécifié. Pour plus d’informations sur les valeurs de DBSTATUS, consultez l' [État](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*ou recherchez DBSTATUS dans OleDb. h.

### <a name="remarks"></a>Remarques

Retourne **`true`** en cas de réussite ou **`false`** d’échec.

## <a name="cdynamicparameteraccessorsetparamstring"></a><a name="setparamstring"></a> CDynamicParameterAccessor :: SetParamString

Définit les données de chaîne du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamString(DBORDINAL nParam,
   constCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,
   constWCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
dans Le numéro de paramètre (décalage de 1). Le paramètre 0 est réservé aux valeurs de retour. Le paramètre number est l’index du paramètre en fonction de son ordre dans l’appel de procédure stockée ou SQL. Pour obtenir un exemple, consultez [setParam](#setparam) .

*pString*<br/>
dans Pointeur vers les données de chaîne ANSI (**char**) ou Unicode (**WCHAR**) du paramètre spécifié. Consultez DBSTATUS dans OleDb. h.

*statut*<br/>
dans État DBSTATUS du paramètre spécifié. Pour plus d’informations sur les valeurs de DBSTATUS, consultez l' [État](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*ou recherchez DBSTATUS dans OleDb. h.

### <a name="remarks"></a>Remarques

Retourne **`true`** en cas de réussite ou **`false`** d’échec.

`SetParamString` échoue si vous tentez de définir une chaîne supérieure à la taille maximale spécifiée pour *pString*.

Utilisez `SetParamString` pour définir des données de paramètre de chaîne dans la mémoire tampon. Utilisez [setParam](#setparam) pour définir des données de paramètre sans chaîne dans la mémoire tampon.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)
