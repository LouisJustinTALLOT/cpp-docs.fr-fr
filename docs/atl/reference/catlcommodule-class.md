---
title: CAtlComModule, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863175"
---
# <a name="catlcommodule-class"></a>CAtlComModule, classe

Cette classe implémente un module serveur COM.

## <a name="syntax"></a>Syntaxe

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|Constructeur.|
|[CAtlComModule :: ~ CAtlComModule](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Appelez cette méthode pour mettre à jour le registre système pour chaque objet du mappage d’objets.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Appelez cette méthode pour inscrire une bibliothèque de types.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Appelez cette méthode pour annuler l’inscription de chaque objet dans la table des objets.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Appelez cette méthode pour annuler l’inscription d’une bibliothèque de types.|

## <a name="remarks"></a>Notes

`CAtlComModule` implémente un module serveur COM, ce qui permet à un client d’accéder aux composants du module.

Cette classe remplace la classe [CComModule](../../atl/reference/ccommodule-class.md) obsolète utilisée dans les versions antérieures d’ATL. Pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

##  <a name="catlcommodule"></a>CAtlComModule::CAtlComModule

Constructeur.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Notes

Initialise le module.

##  <a name="dtor"></a>CAtlComModule :: ~ CAtlComModule

Destructeur.

```
~CAtlComModule();
```

### <a name="remarks"></a>Notes

Libère toutes les fabriques de classes.

##  <a name="registerserver"></a>CAtlComModule::RegisterServer

Appelez cette méthode pour mettre à jour le registre système pour chaque objet du mappage d’objets.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
TRUE si la bibliothèque de types doit être inscrite. La valeur par défaut est FALSE.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet à inscrire. Si la valeur est NULL (valeur par défaut), tous les objets dans le mappage d’objets sont inscrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle la fonction globale [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

##  <a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Appelez cette méthode pour inscrire une bibliothèque de types.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Paramètres

*lpszIndex*<br/>
Chaîne au format «\\\n », où N est l’index d’entier de la ressource TYPELIB.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Ajoute des informations sur une bibliothèque de types au registre système. Si l’instance de module contient plusieurs bibliothèques de types, utilisez la première version de cette méthode pour spécifier la bibliothèque de types à utiliser.

##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer

Appelez cette méthode pour annuler l’inscription de chaque objet dans la table des objets.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
TRUE si l’inscription de la bibliothèque de types doit être annulée. La valeur par défaut est FALSE.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet dont l’inscription doit être annulée. Si la valeur est NULL (valeur par défaut), tous les objets dans le mappage d’objets sont désinscrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Appelle la fonction globale [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

##  <a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Appelez cette méthode pour annuler l’inscription d’une bibliothèque de types.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Paramètres

*lpszIndex*<br/>
Chaîne au format «\\\n », où N est l’index d’entier de la ressource TYPELIB.

### <a name="remarks"></a>Notes

Supprime les informations relatives à une bibliothèque de types du Registre système. Si l’instance de module contient plusieurs bibliothèques de types, utilisez la première version de cette méthode pour spécifier la bibliothèque de types à utiliser.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="see-also"></a>Voir aussi

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
