---
title: Classe CAtlComModule
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
ms.openlocfilehash: 68fdb48edc9304d9d74df6f36bd208cfd35ff307
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321485"
---
# <a name="catlcommodule-class"></a>Classe CAtlComModule

Cette classe implémente un module serveur COM.

## <a name="syntax"></a>Syntaxe

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|Constructeur.|
|[CAtlComModule: :CAtlComModule](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Appelez cette méthode pour mettre à jour le registre du système pour chaque objet dans la carte de l’objet.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Appelez cette méthode pour enregistrer une bibliothèque de type.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Appelez cette méthode pour désenregistrer chaque objet dans la carte de l’objet.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Appelez cette méthode pour désenregistrer une bibliothèque de type.|

## <a name="remarks"></a>Notes

`CAtlComModule`implémente un module serveur COM, permettant à un client d’accéder aux composants du module.

Cette classe remplace la classe [CComModule](../../atl/reference/ccommodule-class.md) obsolète utilisée dans les versions antérieures d’ATL. Voir [les classes de module ATL](../../atl/atl-module-classes.md) pour plus de détails.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlComModule::CAtlComModule

Constructeur.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Notes

Initialise le module.

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlComModule: :CAtlComModule

Destructeur.

```
~CAtlComModule();
```

### <a name="remarks"></a>Notes

Libère toutes les usines de classe.

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlComModule::RegisterServer

Appelez cette méthode pour mettre à jour le registre du système pour chaque objet dans la carte de l’objet.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
VRAI si la bibliothèque de type doit être enregistrée. La valeur par défaut est FALSE.

*pCLSID (en)*<br/>
Indique le CLSID de l’objet à enregistrer. Si NULL (la valeur par défaut), tous les objets de la carte de l’objet seront enregistrés.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appelle la fonction globale [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Appelez cette méthode pour enregistrer une bibliothèque de type.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Paramètres

*lpszIndex*<br/>
Chaîne dans le\\format " N ", où N est l’index integer de la ressource TYPELIB.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Ajoute de l’information sur une bibliothèque type au registre du système. Si l’instance du module contient plusieurs bibliothèques de type, utilisez la première version de cette méthode pour spécifier le type de bibliothèque à utiliser.

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlComModule::UnregisterServer

Appelez cette méthode pour désenregistrer chaque objet dans la carte de l’objet.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
VRAI si la bibliothèque de type doit être non enregistrée. La valeur par défaut est FALSE.

*pCLSID (en)*<br/>
Indique que le CLSID de l’objet n’est pas enregistré. Si NULL (la valeur par défaut), tous les objets de la carte de l’objet ne seront pas enregistrés.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Appelle la fonction globale [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Appelez cette méthode pour désenregistrer une bibliothèque de type.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Paramètres

*lpszIndex*<br/>
Chaîne dans le\\format " N ", où N est l’index integer de la ressource TYPELIB.

### <a name="remarks"></a>Notes

Supprime les informations sur une bibliothèque de type du registre du système. Si l’instance du module contient plusieurs bibliothèques de type, utilisez la première version de cette méthode pour spécifier le type de bibliothèque à utiliser.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="see-also"></a>Voir aussi

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
