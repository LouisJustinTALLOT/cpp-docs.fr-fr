---
title: CAtlModule, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: 798e94aed3bbd98108866ce0a1810485bd68699b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497747"
---
# <a name="catlmodule-class"></a>CAtlModule, classe

Cette classe fournit des méthodes utilisées par plusieurs classes de module ATL.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|Constructeur.|
|[CAtlModule:: ~ CAtlModule](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Substituez cette méthode pour ajouter des paramètres au mappage de remplacement du composant de Registre ATL (Registrar).|
|[CAtlModule::AddTermFunc](#addtermfunc)|Ajoute une nouvelle fonction à appeler lorsque le module se termine.|
|[CAtlModule::GetGITPtr](#getgitptr)|Retourne le pointeur d’interface global.|
|[CAtlModule::GetLockCount](#getlockcount)|Retourne le nombre de verrous.|
|[CAtlModule::Lock](#lock)|Incrémente le nombre de verrous.|
|[CAtlModule::Term](#term)|Libère tous les membres de données.|
|[CAtlModule::Unlock](#unlock)|Décrémente le nombre de verrous.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Cette méthode est appelée par `UpdateRegistryFromResourceD` pour effectuer la mise à jour du Registre.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet. Cette méthode est liée statiquement au composant de Registre ATL.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|Contient le GUID du module actuel.|
|[CAtlModule::m_pGIT](#m_pgit)|Pointeur vers la table d’interface globale.|

## <a name="remarks"></a>Notes

Cette classe est utilisée par la classe [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md), la classe [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)et la [classe CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) pour assurer la prise en charge des applications dll, des applications exe et des services Windows, respectivement.

Pour plus d’informations sur les modules dans ATL, consultez [ATL Module classes](../../atl/atl-module-classes.md).

Cette classe remplace la [classe CComModule](../../atl/reference/ccommodule-class.md) obsolète utilisée dans les versions antérieures d’ATL.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlbase. h

##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements

Substituez cette méthode pour ajouter des paramètres au mappage de remplacement du composant de Registre ATL (Registrar).

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Paramètres

*pRegistrar*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Les paramètres remplaçables permettent au client d’un bureau d’enregistrement de spécifier des données au moment de l’exécution. Pour ce faire, le Bureau d’enregistrement conserve un mappage de remplacement dans lequel il entre les valeurs associées aux paramètres remplaçables dans votre script. Le Bureau d’enregistrement effectue ces entrées au moment de l’exécution.

Pour plus d’informations, consultez la rubrique [utilisation de paramètres remplaçables (le préprocesseur du Bureau d’enregistrement)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) .

##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc

Ajoute une nouvelle fonction à appeler lorsque le module se termine.

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Paramètres

*pFunc*<br/>
Pointeur vers la fonction à ajouter.

*dw*<br/>
Données définies par l’utilisateur, passées à la fonction.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="catlmodule"></a>  CAtlModule::CAtlModule

Constructeur.

```
CAtlModule() throw();
```

### <a name="remarks"></a>Notes

Initialise des membres de données et initie une section critique autour du thread du module.

##  <a name="dtor"></a>  CAtlModule::~CAtlModule

Destructeur.

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Notes

Libère tous les membres de données.

##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr

Récupère un pointeur vers la table d’interface globale.

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Paramètres

*ppGIT*<br/>
Pointeur vers la variable qui recevra le pointeur vers la table d’interface globale.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un code d’erreur en cas d’échec. E_POINTER est retourné si *ppGIT* est égal à null.

### <a name="remarks"></a>Notes

Si l’objet table d’interface globale n’existe pas, il est créé et son adresse est stockée dans la variable membre [CAtlModule:: m_pGIT](#m_pgit).

Dans les versions Debug, une erreur d’assertion se produit si *ppGIT* est égal à null ou si le pointeur de table d’interface globale ne peut pas être obtenu.

Pour plus d’informations sur la table d’interface globale, consultez [IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) .

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

Contient le GUID du module actuel.

```
static GUID m_libid;
```

##  <a name="m_pgit"></a>  CAtlModule::m_pGIT

Pointeur vers la table d’interface globale.

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

Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet.

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
Nom de ressource.

*nResID*<br/>
ID de ressource.

*bRegister*<br/>
TRUE si l’objet doit être enregistré; FALSe dans le cas contraire.

*pMapEntries*<br/>
Pointeur vers la table de remplacement qui stocke les valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement% MODULE%. Pour utiliser des paramètres remplaçables supplémentaires, consultez [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Exécute le script contenu dans la ressource spécifiée par *lpszRes ou nResID*. Si *bRegister* a la valeur true, cette méthode enregistre l’objet dans le registre système; dans le cas contraire, elle supprime l’objet du Registre.

Pour créer un lien statique vers le composant de Registre ATL, consultez [CAtlModule:: UpdateRegistryFromResourceS](#updateregistryfromresources).

Cette méthode appelle [CAtlModule:: UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) et [IRegistrar:: ResourceUnregister](iregistrar-class.md#resourceunregister).

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
Nom de ressource.

*bRegister*<br/>
Indique si l’objet doit être enregistré.

*pMapEntries*<br/>
Pointeur vers la table de remplacement qui stocke les valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement% MODULE%. Pour utiliser des paramètres remplaçables supplémentaires, consultez [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode fournit l’implémentation de [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced).

##  <a name="updateregistryfromresources"></a>  CAtlModule::UpdateRegistryFromResourceS

Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet. Cette méthode est liée statiquement au composant de Registre ATL.

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
ID de ressource.

*lpszRes*<br/>
Nom de ressource.

*bRegister*<br/>
Indique si le script de ressources doit être inscrit.

*pMapEntries*<br/>
Pointeur vers la table de remplacement qui stocke les valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement% MODULE%. Pour utiliser des paramètres remplaçables supplémentaires, consultez [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Semblable à [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced) Except `CAtlModule::UpdateRegistryFromResourceS` crée un lien statique vers le composant de Registre ATL (Registrar).

## <a name="see-also"></a>Voir aussi

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)<br/>
[Composant du Registre (enregistreur)](../../atl/atl-registry-component-registrar.md)
