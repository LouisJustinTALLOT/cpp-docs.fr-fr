---
title: CAtlModule, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
dev_langs:
- C++
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3211f87e2c692c587ee2df82497fc56662e4974d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077281"
---
# <a name="catlmodule-class"></a>CAtlModule, classe

Cette classe fournit des méthodes utilisées par plusieurs classes du module ATL.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|Constructeur.|
|[CAtlModule :: ~ CAtlModule](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Substituez cette méthode pour ajouter des paramètres à la table de remplacement de composant de Registre ATL (inscription).|
|[CAtlModule::AddTermFunc](#addtermfunc)|Ajoute une nouvelle fonction à appeler lorsque le module se termine.|
|[CAtlModule::GetGITPtr](#getgitptr)|Retourne le pointeur d’Interface Global.|
|[CAtlModule::GetLockCount](#getlockcount)|Retourne le nombre de verrous.|
|[CAtlModule::Lock](#lock)|Incrémente le nombre de verrous.|
|[CAtlModule::Term](#term)|Libère tous les membres de données.|
|[CAtlModule::Unlock](#unlock)|Décrémente le nombre de verrous.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Exécute le script contenu dans une ressource spécifiée pour inscrire ou désinscrire un objet.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Cette méthode est appelée par `UpdateRegistryFromResourceD` pour effectuer la mise à jour du Registre.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Exécute le script contenu dans une ressource spécifiée pour inscrire ou désinscrire un objet. Cette méthode lie statiquement au composant de Registre ATL.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|Contient le GUID du module en cours.|
|[CAtlModule::m_pGIT](#m_pgit)|Pointeur vers la Table d’Interface globale.|

## <a name="remarks"></a>Notes

Cette classe est utilisée par [CAtlDllModuleT, classe](../../atl/reference/catldllmodulet-class.md), [CAtlExeModuleT, classe](../../atl/reference/catlexemodulet-class.md), et [CAtlServiceModuleT, classe](../../atl/reference/catlservicemodulet-class.md) pour prendre en charge pour les applications de la DLL, les applications EXE, et Windows services, respectivement.

Pour plus d’informations sur les modules dans ATL, consultez [Module ATL, Classes](../../atl/atl-module-classes.md).

Cette classe remplace obsolète [CComModule (classe)](../../atl/reference/ccommodule-class.md) utilisé dans les versions antérieures de l’ATL.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements

Substituez cette méthode pour ajouter des paramètres à la table de remplacement de composant de Registre ATL (inscription).

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Paramètres

*pRegistrar*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Paramètres remplaçables autoriser le client du bureau d’enregistrement spécifier les données d’exécution. Pour ce faire, le bureau d’enregistrement gère un mappage de remplacement dans laquelle il entre les valeurs associées aux paramètres remplaçables dans votre script. Le bureau d’enregistrement effectue ces entrées au moment de l’exécution.

Consultez la rubrique [à l’aide des paramètres remplaçables (le préprocesseur de Registrar)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) pour plus d’informations.

##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc

Ajoute une nouvelle fonction à appeler lorsque le module se termine.

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Paramètres

*pFunc*<br/>
Pointeur vers la fonction à ajouter.

*entrepôt de données*<br/>
Les données définies par l’utilisateur, passé à la fonction.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="catlmodule"></a>  CAtlModule::CAtlModule

Constructeur.

```
CAtlModule() throw();
```

### <a name="remarks"></a>Notes

Initialise les membres de données et lance une section critique autour de thread du module.

##  <a name="dtor"></a>  CAtlModule :: ~ CAtlModule

Destructeur.

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Notes

Libère tous les membres de données.

##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr

Récupère un pointeur vers la Table d’Interface globale.

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Paramètres

*ppGIT*<br/>
Pointeur vers la variable qui reçoit le pointeur vers la Table d’Interface globale.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite ou un code d’erreur en cas d’échec. E_POINTER est retournée si *ppGIT* est égal à NULL.

### <a name="remarks"></a>Notes

Si l’objet Global Interface Table n’existe pas, il est créé, et son adresse est stockée dans la variable membre [CAtlModule::m_pGIT](#m_pgit).

Dans les versions debug, une erreur d’assertion se produit si *ppGIT* est égal à NULL, ou si le pointeur de la Table d’Interface globale ne peut pas être obtenu.

Consultez [IGlobalInterfaceTable](/windows/desktop/api/objidl/nn-objidl-iglobalinterfacetable) pour plus d’informations sur la Table d’Interface globale.

##  <a name="getlockcount"></a>  CAtlModule::GetLockCount

Retourne le nombre de verrous.

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de verrous. Cette valeur peut être utile pour les diagnostics et le débogage.

##  <a name="lock"></a>  CAtlModule::Lock

Incrémente le nombre de verrous.

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Valeur de retour

Incrémente le nombre de verrous et retourne la valeur mise à jour. Cette valeur peut être utile pour les diagnostics et le débogage.

##  <a name="m_libid"></a>  CAtlModule::m_libid

Contient le GUID du module en cours.

```
static GUID m_libid;
```

##  <a name="m_pgit"></a>  CAtlModule::m_pGIT

Pointeur vers la Table d’Interface globale.

```
IGlobalInterfaceTable* m_pGIT;
```

##  <a name="term"></a>  CAtlModule::Term

Libère tous les membres de données.

```
void Term() throw();
```

### <a name="remarks"></a>Notes

Libère tous les membres de données. Cette méthode est appelée par le destructeur.

##  <a name="unlock"></a>  CAtlModule::Unlock

Décrémente le nombre de verrous.

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Décrémente le nombre de verrous et retourne la valeur mise à jour. Cette valeur peut être utile pour les diagnostics et le débogage.

##  <a name="updateregistryfromresourced"></a>  CAtlModule::UpdateRegistryFromResourceD

Exécute le script contenu dans une ressource spécifiée pour inscrire ou désinscrire un objet.

```
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*lpszRes*<br/>
Un nom de ressource.

*nResID*<br/>
Un ID de ressource.

*bRegister*<br/>
TRUE si l’objet doit être inscrit ; FALSE sinon.

*pMapEntries*<br/>
Pointeur vers la table de remplacement stocker des valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement le MODULE %. Pour utiliser les paramètres remplaçables supplémentaires, consultez [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Exécute le script contenu dans la ressource spécifiée par *lpszRes ou nResID*. Si *bRegister* a la valeur TRUE, cette méthode inscrit l’objet dans le Registre système ; sinon, elle supprime l’objet à partir du Registre.

Pour lier statiquement au composant de Registre ATL (inscription), consultez [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).

Cette méthode appelle [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) et [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).

##  <a name="updateregistryfromresourcedhelper"></a>  CAtlModule::UpdateRegistryFromResourceDHelper

Cette méthode est appelée par `UpdateRegistryFromResourceD` pour effectuer la mise à jour du Registre.

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*lpszRes*<br/>
Un nom de ressource.

*bRegister*<br/>
Indique si l’objet doit être inscrite.

*pMapEntries*<br/>
Pointeur vers la table de remplacement stocker des valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement le MODULE %. Pour utiliser les paramètres remplaçables supplémentaires, consultez [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode fournit l’implémentation de [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced).

##  <a name="updateregistryfromresources"></a>  CAtlModule::UpdateRegistryFromResourceS

Exécute le script contenu dans une ressource spécifiée pour inscrire ou désinscrire un objet. Cette méthode lie statiquement au composant de Registre ATL.

```
HRESULT WINAPI UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*nResID*<br/>
Un ID de ressource.

*lpszRes*<br/>
Un nom de ressource.

*bRegister*<br/>
Indique si le script de ressources doit être inscrite.

*pMapEntries*<br/>
Pointeur vers la table de remplacement stocker des valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement le MODULE %. Pour utiliser les paramètres remplaçables supplémentaires, consultez [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Semblable à [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) sauf `CAtlModule::UpdateRegistryFromResourceS` crée un lien statique vers le composant de Registre ATL (inscription).

## <a name="see-also"></a>Voir aussi

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)<br/>
[Composant de Registre (inscription)](../../atl/atl-registry-component-registrar.md)
