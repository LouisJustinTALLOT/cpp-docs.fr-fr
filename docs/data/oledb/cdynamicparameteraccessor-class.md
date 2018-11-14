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
ms.openlocfilehash: c2cc67e6e837844356a071aa362dcca85eca24e4
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556970"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor (classe)

Semblable à [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) mais obtient les informations sur les paramètres à définir en appelant l’interface [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) .

## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>Configuration requise

**En-tête**: atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
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

## <a name="remarks"></a>Notes

Le fournisseur doit prendre en charge `ICommandWithParameters` pour permettre au consommateur d’utiliser cette classe.

Les informations sur les paramètres sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenez les données de paramètre à partir de la mémoire tampon via [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) et [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Pour obtenir un exemple qui montre comment utiliser cette classe pour exécuter une procédure stockée SQL Server et d’obtenir les valeurs de paramètre de sortie, consultez le [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) exemple de code dans le [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) référentiel sur GitHub.

## <a name="cdynamicparameteraccessor"></a> CDynamicParameterAccessor::CDynamicParameterAccessor

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
Spécifie la façon dont les données BLOB doit être gérée. La valeur par défaut est DBBLOBHANDLING_DEFAULT. Consultez [CDynamicAccessor::SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) pour obtenir une description des valeurs DBBLOBHANDLINGENUM.

*nBlobSize*<br/>
La taille maximale de BLOB en octets ; données de la colonne par rapport à cette valeur sont traitées comme un objet BLOB. La valeur par défaut est 8 000. Consultez [CDynamicAccessor::SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) pour plus d’informations.

### <a name="remarks"></a>Notes

Consultez le [CDynamicAccessor::CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) constructeur pour plus d’informations sur la gestion des objets BLOB.

## <a name="getparam"></a> CDynamicParameterAccessor::GetParam

Récupère les données de chaîne pour un paramètre spécifié à partir de la mémoire tampon de paramètre.

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
Un paramètre basé sur un modèle qui est le type de données.

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*pParamName*<br/>
[in] Le nom du paramètre.

*pData*<br/>
[out] Pointeur vers la mémoire contenant les données récupérées à partir de la mémoire tampon.

### <a name="return-value"></a>Valeur de retour

Pour les versions non, pointe vers la mémoire contenant les données récupérées à partir de la mémoire tampon. Pour les versions basées sur un modèle, retourne **true** en cas de réussite ou **false** en cas d’échec.

Utilisez `GetParam` pour récupérer des données de paramètre de chaîne à partir de la mémoire tampon. Utilisez [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) pour récupérer des données de paramètre de chaîne à partir de la mémoire tampon.

## <a name="getparamcount"></a> CDynamicParameterAccessor::GetParamCount

Récupère le nombre de paramètres stockés dans la mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de paramètres.

## <a name="getparamio"></a> CDynamicParameterAccessor::GetParamIO

Détermine si le paramètre spécifié est un paramètre d’entrée ou de sortie.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*pParamIO*<br/>
Un pointeur vers la variable contenant le `DBPARAMIO` (entrée ou sortie) de type du paramètre spécifié. Il est défini comme suit :

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>Valeur de retour

Retourne **true** en cas de réussite ou **false** en cas d’échec.

## <a name="getparamlength"></a> CDynamicParameterAccessor::GetParamLength

Récupère la longueur du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*pLength*<br/>
[out] Pointeur vers la variable contenant la longueur en octets du paramètre spécifié.

### <a name="remarks"></a>Notes

Le premier remplacement retourne **true** en cas de réussite ou **false** en cas d’échec. Le deuxième remplacement pointe vers la mémoire qui contient la longueur du paramètre.

## <a name="getparamname"></a> CDynamicParameterAccessor::GetParamName

Récupère le nom du paramètre spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

### <a name="return-value"></a>Valeur de retour

Le nom du paramètre spécifié.

## <a name="getparamstatus"></a> CDynamicParameterAccessor::GetParamStatus

Récupère l’état du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*pStatus*<br/>
[out] Pointeur vers la variable qui contient l’état DBSTATUS du paramètre spécifié. Pour plus d’informations sur les valeurs DBSTATUS, consultez [état](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *de référence du programmeur OLE DB*, ou recherchez DBSTATUS dans oledb.h.

### <a name="remarks"></a>Notes

Le premier remplacement retourne **true** en cas de réussite ou **false** en cas d’échec. Le deuxième remplacement pointe vers la mémoire contenant l’état du paramètre spécifié.

## <a name="getparamstring"></a> CDynamicParameterAccessor::GetParamString

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
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*strOutput*<br/>
[out] L’ANSI (`CSimpleStringA`) ou Unicode (`CSimpleStringW`) les données du paramètre spécifié de type string. Vous devez passer un paramètre de type `CString`, par exemple :

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
[out] Un pointeur vers l’ANSI (**CHAR**) ou Unicode (**WCHAR**) les données du paramètre spécifié de type string.

*pMaxLen*<br/>
[out] Un pointeur vers la taille de la mémoire tampon vers laquelle pointe *pBuffer* (en caractères, y compris le caractère NULL de fin).

### <a name="remarks"></a>Notes

Retourne **true** en cas de réussite ou **false** en cas d’échec.

Si *pBuffer* est NULL, cette méthode définit la taille de mémoire tampon requise dans la mémoire vers laquelle pointée *pMaxLen* et retourner **true** sans copier les données.

Cette méthode échoue si la mémoire tampon *pBuffer* n’est pas assez grand pour contenir la chaîne entière.

Utilisez `GetParamString` pour récupérer des données de paramètre de chaîne à partir de la mémoire tampon. Utilisez [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) pour récupérer des données de paramètre de chaîne à partir de la mémoire tampon.

## <a name="getparamtype"></a> CDynamicParameterAccessor::GetParamType

Récupère le type de données d’un paramètre spécifique.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*PTapez*<br/>
[out] Pointeur vers la variable qui contient le type de données du paramètre spécifié.

### <a name="return-value"></a>Valeur de retour

Retourne **true** en cas de réussite ou **false** en cas d’échec.

## <a name="setparam"></a> CDynamicParameterAccessor::SetParam

Définit la mémoire tampon de paramètre en utilisant les données (non-chaînées) spécifiées.

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
Un paramètre basé sur un modèle qui est le type de données.

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Exemple :

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pParamName*<br/>
[in] Le nom du paramètre.

*pData*<br/>
[in] Pointeur vers la mémoire contenant les données à écrire dans la mémoire tampon.

*status*<br/>
[in] L’état de la colonne DBSTATUS. Pour plus d’informations sur les valeurs DBSTATUS, consultez [état](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *de référence du programmeur OLE DB*, ou recherchez DBSTATUS dans oledb.h.

### <a name="return-value"></a>Valeur de retour

Retourne **true** en cas de réussite ou **false** en cas d’échec.

Utilisez `SetParam` pour définir les données de paramètre de chaîne dans la mémoire tampon. Utilisez [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) de définir les données de paramètre de chaîne dans la mémoire tampon.

## <a name="setparamlength"></a> CDynamicParameterAccessor::SetParamLength

Définit la longueur du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*length*<br/>
[in] La longueur en octets du paramètre spécifié.

### <a name="remarks"></a>Notes

Retourne **true** en cas de réussite ou **false** en cas d’échec.

## <a name="setparamstatus"></a> CDynamicParameterAccessor::SetParamStatus

Définit l’état du paramètre spécifié stocké en mémoire tampon.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>Paramètres

*nParam*<br/>
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*status*<br/>
[in] L’état DBSTATUS du paramètre spécifié. Pour plus d’informations sur les valeurs DBSTATUS, consultez [état](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *de référence du programmeur OLE DB*, ou recherchez DBSTATUS dans oledb.h.

### <a name="remarks"></a>Notes

Retourne **true** en cas de réussite ou **false** en cas d’échec.

## <a name="setparamstring"></a> CDynamicParameterAccessor::SetParamString

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
[in] Le numéro de paramètre (offset à partir de 1). Le paramètre 0 est réservé pour les valeurs de retour. Le paramètre est l’index du paramètre en fonction de sa position dans le SQL ou d’un appel de procédure stockée. Consultez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour obtenir un exemple.

*pString*<br/>
[in] Un pointeur vers l’ANSI (**CHAR**) ou Unicode (**WCHAR**) les données du paramètre spécifié de type string. Consultez DBSTATUS dans oledb.h.

*status*<br/>
[in] L’état DBSTATUS du paramètre spécifié. Pour plus d’informations sur les valeurs DBSTATUS, consultez [état](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *de référence du programmeur OLE DB*, ou recherchez DBSTATUS dans oledb.h.

### <a name="remarks"></a>Notes

Retourne **true** en cas de réussite ou **false** en cas d’échec.

`SetParamString` échoue si vous essayez de définir une chaîne qui est supérieure à la taille maximale spécifiée pour *pString*.

Utilisez `SetParamString` pour définir les données de paramètre de chaîne dans la mémoire tampon. Utilisez [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) pour définir les données de paramètre de chaîne dans la mémoire tampon.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, classe](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)