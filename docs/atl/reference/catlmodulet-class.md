---
title: Classe CAtlModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: bf64c073249b7426fafb430a708573d9d06d11fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321414"
---
# <a name="catlmodulet-class"></a>Classe CAtlModuleT

Cette classe implémente un module ATL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe `CAtlModuleT`dérivée de .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlModulet::CAtlModulet](#catlmodulet)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Initialise le membre des données contenant le GUID du module actuel.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Ajoute l’EXE au registre.|
|[CAtlModuleT::RegisterServer](#registerserver)|Ajoute le service au registre.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Supprime l’EXE du registre.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Supprime le service du registre.|
|[CAtlModuleT::Mise à jourRegistryAppId](#updateregistryappid)|Mise à jour des informations EXE dans le registre.|

## <a name="remarks"></a>Notes

`CAtlModuleT`, dérivé de [CAtlModule](../../atl/reference/catlmodule-class.md), implémente un module ATL Exécutantable (EXE) ou service (EXE). Un module Exécutable est un serveur local hors-processus, tandis qu’un module de service est une application Windows qui s’exécute en arrière-plan lorsque Windows démarre.

`CAtlModuleT`fournit un soutien pour l’initialisation, l’enregistrement et le non-enregistrement du module.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModulet::CAtlModulet

Constructeur.

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Notes

Appels [CAtlModulet::InitLibId](#initlibid).

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId

Initialise le membre des données contenant le GUID du module actuel.

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Notes

Appelé par le constructeur [CAtlModuleT::CAtlModuleT](#catlmodulet).

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

Ajoute l’EXE au registre.

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

Ajoute le service au registre.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
VRAI si la bibliothèque de type doit être enregistrée. La valeur par défaut est FALSE.

*pCLSID (en)*<br/>
Indique le CLSID de l’objet à enregistrer. Si NULL (la valeur par défaut), tous les objets de la carte de l’objet seront enregistrés.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId

Supprime l’EXE du registre.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer

Supprime le service du registre.

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
VRAI si la bibliothèque de type doit également être non enregistrée.

*pCLSID (en)*<br/>
Indique que le CLSID de l’objet n’est pas enregistré. Si NULL (la valeur par défaut), tous les objets de la carte de l’objet ne seront pas enregistrés.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::Mise à jourRegistryAppId

Mise à jour des informations EXE dans le registre.

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Paramètres

*bRegister (en)*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="see-also"></a>Voir aussi

[Classe CAtlModule](../../atl/reference/catlmodule-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de modules](../../atl/atl-module-classes.md)
