---
description: 'En savoir plus sur : classe CAtlModuleT'
title: CAtlModuleT, classe
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
ms.openlocfilehash: 841d4a41b7df818d9e966af1050fd9e376d89447
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147223"
---
# <a name="catlmodulet-class"></a>CAtlModuleT, classe

Cette classe implémente un module ATL.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `CAtlModuleT` .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Initialise les données membres contenant le GUID du module en cours.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Ajoute l’EXE au registre.|
|[CAtlModuleT::RegisterServer](#registerserver)|Ajoute le service au registre.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Supprime le fichier EXE du Registre.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Supprime le service du Registre.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Met à jour les informations de l’EXE dans le registre.|

## <a name="remarks"></a>Notes

`CAtlModuleT`, dérivé de [CAtlModule](../../atl/reference/catlmodule-class.md), implémente un module exécutable (exe) ou un module ATL de service (exe). Un module exécutable est un serveur local, hors processus, alors qu’un module de service est une application Windows qui s’exécute en arrière-plan au démarrage de Windows.

`CAtlModuleT` fournit la prise en charge de l’initialisation, de l’inscription et de l’annulation de l’inscription du module.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a> CAtlModuleT::CAtlModuleT

Constructeur.

```cpp
CAtlModuleT() throw();
```

### <a name="remarks"></a>Notes

Appelle [CAtlModuleT :: InitLibId](#initlibid).

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a> CAtlModuleT::InitLibId

Initialise les données membres contenant le GUID du module en cours.

```cpp
static void InitLibId() throw();
```

### <a name="remarks"></a>Notes

Appelée par le constructeur [CAtlModuleT :: CAtlModuleT](#catlmodulet).

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a> CAtlModuleT::RegisterAppId

Ajoute l’EXE au registre.

```cpp
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a> CAtlModuleT::RegisterServer

Ajoute le service au registre.

```cpp
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
TRUE si la bibliothèque de types doit être inscrite. La valeur par défaut est FALSE.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet à inscrire. Si la valeur est NULL (valeur par défaut), tous les objets dans le mappage d’objets sont inscrits.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a> CAtlModuleT::UnregisterAppId

Supprime le fichier EXE du Registre.

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a> CAtlModuleT::UnregisterServer

Supprime le service du Registre.

```cpp
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
TRUE si l’inscription de la bibliothèque de types doit également être annulée.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet dont l’inscription doit être annulée. Si la valeur est NULL (valeur par défaut), tous les objets dans le mappage d’objets sont désinscrits.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a> CAtlModuleT::UpdateRegistryAppId

Met à jour les informations de l’EXE dans le registre.

```cpp
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Paramètres

*bRegister*<br/>
Réservé.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="see-also"></a>Voir aussi

[CAtlModule, classe](../../atl/reference/catlmodule-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
