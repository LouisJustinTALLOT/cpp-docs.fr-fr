---
title: Classe CAtlModule
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
ms.openlocfilehash: cfc11a95a8d5d9354279f4c71698a6bc35c7aca7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748621"
---
# <a name="catlmodule-class"></a>Classe CAtlModule

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
|[CAtlModule: :CAtlModule](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlModule::AddCommonRGSRéplacements](#addcommonrgsreplacements)|Remplacer cette méthode pour ajouter des paramètres à la carte de remplacement du composant du registre ATL (registraire).|
|[CAtlModule::AddTermFunc](#addtermfunc)|Ajoute une nouvelle fonction à appeler lorsque le module se termine.|
|[CAtlModule::GetGITPtr](#getgitptr)|Retourne le pointeur d’interface globale.|
|[CAtlModule::GetLockCount](#getlockcount)|Retourne le nombre de serrures.|
|[CAtlModule::Lock](#lock)|Incréments le nombre de serrures.|
|[CAtlModule::Terme](#term)|Communiqués à tous les membres des données.|
|[CAtlModule::Unlock](#unlock)|Décrémente le nombre de verrous.|
|[CAtlModule::UpdateRegistryDeResourceD](#updateregistryfromresourced)|Exécute le script contenu dans une ressource spécifiée pour enregistrer ou désinscrire un objet.|
|[CAtlModule::UpdateRegistryDeResourceDHelper](#updateregistryfromresourcedhelper)|Cette méthode est `UpdateRegistryFromResourceD` appelée pour effectuer la mise à jour du registre.|
|[CAtlModule::UpdateRegistryDeResourceS](#updateregistryfromresources)|Exécute le script contenu dans une ressource spécifiée pour enregistrer ou désinscrire un objet. Cette méthode relie statiquement le composant du registre ATL.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|Contient le GUID du module actuel.|
|[CAtlModule::m_pGIT](#m_pgit)|Pointeur vers la Table d’interface globale.|

## <a name="remarks"></a>Notes

Cette classe est utilisée par [CAtlDllModuleT Class](../../atl/reference/catldllmodulet-class.md), [CAtlExeModuleT Class](../../atl/reference/catlexemodulet-class.md), et [CAtlServiceModuleT Class](../../atl/reference/catlservicemodulet-class.md) pour fournir un support pour les applications DLL, les applications EXE et les services Windows, respectivement.

Pour plus d’informations sur les modules dans ATL, voir [atL Module Classes](../../atl/atl-module-classes.md).

Cette classe remplace la [classe CComModule](../../atl/reference/ccommodule-class.md) obsolète utilisée dans les versions antérieures d’ATL.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSRéplacements

Remplacer cette méthode pour ajouter des paramètres à la carte de remplacement du composant du registre ATL (registraire).

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Paramètres

*pRegistraire*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Les paramètres remplaçables permettent au client d’un registraire de spécifier les données en temps de fonctionnement. Pour ce faire, le registraire maintient une carte de remplacement dans laquelle il entre les valeurs associées aux paramètres remplaçables de votre script. Le registraire fait ces entrées au moment de l’exécution.

Consultez le sujet [à l’aide de paramètres remplaçables (préprocesseur du registraire)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) pour plus de détails.

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtlModule::AddTermFunc

Ajoute une nouvelle fonction à appeler lorsque le module se termine.

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Paramètres

*pFunc (pFunc)*<br/>
Pointeur à la fonction à ajouter.

*dw*<br/>
Données définies par l’utilisateur, transmises à la fonction.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtlModule::CAtlModule

Constructeur.

```
CAtlModule() throw();
```

### <a name="remarks"></a>Notes

Initialise les membres des données et initie une section critique autour du fil du module.

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtlModule: :CAtlModule

Destructeur.

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Notes

Communiqués à tous les membres des données.

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtlModule::GetGITPtr

Récupère un pointeur sur la Table d’interface globale.

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Paramètres

*ppGIT*<br/>
Pointeur vers la variable qui recevra le pointeur à la Table d’interface globale.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou un code d’erreur sur l’échec. E_POINTER est retourné si *ppGIT* est égal à NULL.

### <a name="remarks"></a>Notes

Si l’objet Global Interface Table n’existe pas, il est créé, et son adresse est stockée dans la variable membre [CAtlModule::m_pGIT](#m_pgit).

Dans les constructions de débog, une erreur d’affirmation se produira si *ppGIT* est égal à NULL, ou si le pointeur global de table d’interface ne peut pas être obtenu.

Voir [IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) pour plus d’informations sur la Table d’interface mondiale.

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtlModule::GetLockCount

Retourne le nombre de serrures.

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de serrures. Cette valeur peut être utile pour le diagnostic et le débogage.

## <a name="catlmodulelock"></a><a name="lock"></a>CAtlModule::Lock

Incréments le nombre de serrures.

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Valeur de retour

Incréments le nombre de verrouillages et retourne la valeur mise à jour. Cette valeur peut être utile pour le diagnostic et le débogage.

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModule::m_libid

Contient le GUID du module actuel.

```
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModule::m_pGIT

Pointeur vers la Table d’interface globale.

```
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtlModule::Terme

Communiqués à tous les membres des données.

```cpp
void Term() throw();
```

### <a name="remarks"></a>Notes

Communiqués à tous les membres des données. Cette méthode est appelée par le destructeur.

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtlModule::Unlock

Décrémente le nombre de verrous.

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Décroisse le nombre de verrous et retourne la valeur mise à jour. Cette valeur peut être utile pour le diagnostic et le débogage.

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryDeResourceD

Exécute le script contenu dans une ressource spécifiée pour enregistrer ou désinscrire un objet.

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

*nResID (en)*<br/>
Une pièce d’identité de ressource.

*bRegister (en)*<br/>
VRAI si l’objet doit être enregistré; FALSE autrement.

*pMapEntries (en)*<br/>
Un pointeur sur la carte de remplacement stockant les valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement %MODULE%. Pour utiliser d’autres paramètres remplaçables, voir [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Exécute le script contenu dans la ressource spécifiée par *lpszRes ou nResID*. Si *bRegister* est VRAI, cette méthode enregistre l’objet dans le registre du système; sinon il supprime l’objet du registre.

Pour établir un lien statique vers le composant du registre ATL (registraire), voir [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).

Cette méthode appelle [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) et [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryDeResourceDHelper

Cette méthode est `UpdateRegistryFromResourceD` appelée pour effectuer la mise à jour du registre.

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*lpszRes*<br/>
Un nom de ressource.

*bRegister (en)*<br/>
Indique si l’objet doit être enregistré.

*pMapEntries (en)*<br/>
Un pointeur sur la carte de remplacement stockant les valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement %MODULE%. Pour utiliser d’autres paramètres remplaçables, voir [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode fournit la mise en œuvre de [CAtlModule::UpdateRegistryDeResourceD](#updateregistryfromresourced).

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryDeResourceS

Exécute le script contenu dans une ressource spécifiée pour enregistrer ou désinscrire un objet. Cette méthode relie statiquement le composant du registre ATL.

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

*nResID (en)*<br/>
Une pièce d’identité de ressource.

*lpszRes*<br/>
Un nom de ressource.

*bRegister (en)*<br/>
Indique si le script de ressource doit être enregistré.

*pMapEntries (en)*<br/>
Un pointeur sur la carte de remplacement stockant les valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement %MODULE%. Pour utiliser d’autres paramètres remplaçables, voir [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Semblable à [CAtlModule::UpdateRegistryDeResourceD,](#updateregistryfromresourced) sauf `CAtlModule::UpdateRegistryFromResourceS` crée un lien statique vers le composant du registre ATL (registraire).

## <a name="see-also"></a>Voir aussi

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de modules](../../atl/atl-module-classes.md)<br/>
[Composant du Registre (enregistreur)](../../atl/atl-registry-component-registrar.md)
