---
title: CAtlDllModuleT, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: be42915c6c2e941bc5fc1de78c5c7ac26ccca6e2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259215"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT, classe

Cette classe représente le module pour une DLL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe dérivée de `CAtlDllModuleT`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Constructeur.|
|[CAtlDllModuleT::~CAtlDllModuleT](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Teste si la DLL peut être déchargée.|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Retourne une fabrique de classe.|
|[CAtlDllModuleT::DllMain](#dllmain)|Point d’entrée facultative dans une bibliothèque de liens dynamiques (DLL).|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Ajoute des entrées dans le Registre système pour les objets dans la DLL.|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Supprime les entrées dans le Registre système pour les objets dans la DLL.|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Retourne une fabrique de classe. Appelée par [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Notes

`CAtlDllModuleT` représente le module pour une bibliothèque de liens dynamiques (DLL) et fournit des fonctions utilisées par tous les projets DLL. Cette spécialisation de [CAtlModuleT](../../atl/reference/catlmodulet-class.md) classe inclut la prise en charge pour l’inscription.

Pour plus d’informations sur les modules dans ATL, consultez [Module ATL, Classes](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase.h

##  <a name="catldllmodulet"></a>  CAtlDllModuleT::CAtlDllModuleT

Constructeur.

```
CAtlDllModuleT() throw();
```

##  <a name="dtor"></a>  CAtlDllModuleT::~CAtlDllModuleT

Destructeur.

```
~CAtlDllModuleT() throw();
```

##  <a name="dllcanunloadnow"></a>  CAtlDllModuleT::DllCanUnloadNow

Teste si la DLL peut être déchargée.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK si la DLL peut être déchargée ou S_FALSE s’il ne peut pas.

##  <a name="dllgetclassobject"></a>  CAtlDllModuleT::DllGetClassObject

Retourne la fabrique de classe.

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
Le CLSID de l’objet doit être créé.

*riid*<br/>
IID de l’interface demandée.

*ppv*<br/>
Un pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppv* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain

Point d’entrée facultative dans une bibliothèque de liens dynamiques (DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Paramètres

*dwReason*<br/>
Si défini sur les appels de notification DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH et DLL_THREAD_DETACH est désactivé.

*lpReserved*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Renvoie toujours TRUE.

### <a name="remarks"></a>Notes

La désactivation de la DLL_THREAD_ATTACH et DLL_THREAD_DETACH notification appels peuvent être une optimisation utile pour les applications multithread qui ont de nombreuses DLL, qui souvent de créer et supprimer des threads, et dont les DLL n’avez pas besoin de ces notifications au niveau du thread de pièce jointe/le détachement.

##  <a name="dllregisterserver"></a>  CAtlDllModuleT::DllRegisterServer

Ajoute des entrées dans le Registre système pour les objets dans la DLL.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
TRUE si la bibliothèque de types doit être enregistré. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer

Supprime les entrées dans le Registre système pour les objets dans la DLL.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
TRUE si la bibliothèque de types doit être supprimé à partir du Registre. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="getclassobject"></a>  CAtlDllModuleT::GetClassObject

Crée un objet du CLSID spécifié.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
Le CLSID de l’objet doit être créé.

*riid*<br/>
IID de l’interface demandée.

*ppv*<br/>
Un pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppv* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode est appelée par [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) et est inclus pour la compatibilité descendante.

## <a name="see-also"></a>Voir aussi

[CAtlModuleT, classe](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT, classe](../../atl/reference/catlexemodulet-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
