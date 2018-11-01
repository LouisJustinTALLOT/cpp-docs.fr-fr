---
title: Catlmodulet, classe
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
ms.openlocfilehash: 0d7673d634bad2d20dae63e4293f12e5530c4acd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534899"
---
# <a name="catlmodulet-class"></a>Catlmodulet, classe

Cette classe implémente un module d’ATL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe dérivée de `CAtlModuleT`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Initialise le membre de données qui contient le GUID du module en cours.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Ajoute le fichier EXE dans le Registre.|
|[CAtlModuleT::RegisterServer](#registerserver)|Ajoute le service dans le Registre.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Supprime le fichier EXE à partir du Registre.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Supprime le service à partir du Registre.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Met à jour les informations de l’EXE dans le Registre.|

## <a name="remarks"></a>Notes

`CAtlModuleT`, dérivé [CAtlModule](../../atl/reference/catlmodule-class.md), implémente un fichier exécutable (EXE) ou un module de Service (EXE) ATL. Un module exécutable est un serveur local, out-of-process, tandis qu’un module de Service est une application Windows qui s’exécute en arrière-plan au démarrage de Windows.

`CAtlModuleT` prend en charge l’initialisation, l’inscription et la désinscription du module.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="catlmodulet"></a>  CAtlModuleT::CAtlModuleT

Constructeur.

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Notes

Appels [CAtlModuleT::InitLibId](#initlibid).

##  <a name="initlibid"></a>  CAtlModuleT::InitLibId

Initialise le membre de données qui contient le GUID du module en cours.

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Notes

Appelé par le constructeur [CAtlModuleT::CAtlModuleT](#catlmodulet).

##  <a name="registerappid"></a>  CAtlModuleT::RegisterAppId

Ajoute le fichier EXE dans le Registre.

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="registerserver"></a>  CAtlModuleT::RegisterServer

Ajoute le service dans le Registre.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
TRUE si la bibliothèque de types doit être enregistré. La valeur par défaut est FALSE.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet à inscrire. Si NULL (la valeur par défaut), tous les objets du mappage d’objets sera inscrit.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="unregisterappid"></a>  CAtlModuleT::UnregisterAppId

Supprime le fichier EXE à partir du Registre.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="unregisterserver"></a>  CAtlModuleT::UnregisterServer

Supprime le service à partir du Registre.

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
TRUE si la bibliothèque de types doit également être annulée.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet doit être annulée. Si la valeur NULL (la valeur par défaut), tous les objets du mappage d’objets sera annulée.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="updateregistryappid"></a>  CAtlModuleT::UpdateRegistryAppId

Met à jour les informations de l’EXE dans le Registre.

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Paramètres

*bRegister*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

## <a name="see-also"></a>Voir aussi

[CAtlModule, classe](../../atl/reference/catlmodule-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
