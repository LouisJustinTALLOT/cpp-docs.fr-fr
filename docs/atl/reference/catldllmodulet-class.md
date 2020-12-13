---
description: 'En savoir plus sur : classe CAtlDllModuleT'
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
ms.openlocfilehash: b6b6f87fc77187b150824fcd67fae254eb6d8f57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147431"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT, classe

Cette classe représente le module pour une DLL.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe dérivée de `CAtlDllModuleT` .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlDllModuleT :: CAtlDllModuleT](#catldllmodulet)|Constructeur.|
|[CAtlDllModuleT :: ~ CAtlDllModuleT](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlDllModuleT ::D llCanUnloadNow](#dllcanunloadnow)|Teste si la DLL peut être déchargée.|
|[CAtlDllModuleT ::D llGetClassObject](#dllgetclassobject)|Retourne une fabrique de classe.|
|[CAtlDllModuleT ::D llMain](#dllmain)|Point d’entrée facultatif dans une bibliothèque de liens dynamiques (DLL).|
|[CAtlDllModuleT ::D llRegisterServer](#dllregisterserver)|Ajoute des entrées à la Registre système pour les objets dans la DLL.|
|[CAtlDllModuleT ::D llUnregisterServer](#dllunregisterserver)|Supprime les entrées du Registre système pour les objets de la DLL.|
|[CAtlDllModuleT :: GetClassObject,](#getclassobject)|Retourne une fabrique de classe. Appelé par [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Notes

`CAtlDllModuleT` représente le module d’une bibliothèque de liens dynamiques (DLL) et fournit les fonctions utilisées par tous les projets DLL. Cette spécialisation de la classe [CAtlModuleT](../../atl/reference/catlmodulet-class.md) prend en charge l’inscription.

Pour plus d’informations sur les modules dans ATL, consultez [ATL Module classes](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a> CAtlDllModuleT :: CAtlDllModuleT

Constructeur.

```cpp
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a> CAtlDllModuleT :: ~ CAtlDllModuleT

Destructeur.

```cpp
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a> CAtlDllModuleT ::D llCanUnloadNow

Teste si la DLL peut être déchargée.

```cpp
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK si la DLL peut être déchargée, ou S_FALSE si elle ne le peut pas.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a> CAtlDllModuleT ::D llGetClassObject

Retourne la fabrique de classe.

```cpp
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
CLSID de l’objet à créer.

*riid*<br/>
IID de l’interface demandée.

*ppv*<br/>
Pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *PPV* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a> CAtlDllModuleT ::D llMain

Point d’entrée facultatif dans une bibliothèque de liens dynamiques (DLL).

```cpp
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Paramètres

*dwReason*<br/>
Si la valeur est DLL_PROCESS_ATTACH, les appels de notification DLL_THREAD_ATTACH et DLL_THREAD_DETACH sont désactivés.

*lpReserved*<br/>
Réservé.

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

La désactivation des appels de notification DLL_THREAD_ATTACH et DLL_THREAD_DETACH peut être une optimisation utile pour les applications multithread qui possèdent de nombreuses dll, qui créent et suppriment fréquemment des threads, et dont les dll n’ont pas besoin de ces notifications au niveau du thread pour la connexion/le détachement.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a> CAtlDllModuleT ::D llRegisterServer

Ajoute des entrées à la Registre système pour les objets dans la DLL.

```cpp
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
TRUE si la bibliothèque de types doit être inscrite. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a> CAtlDllModuleT ::D llUnregisterServer

Supprime les entrées du Registre système pour les objets de la DLL.

```cpp
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
TRUE si la bibliothèque de types doit être supprimée du Registre. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a> CAtlDllModuleT :: GetClassObject,

Crée un objet du CLSID spécifié.

```cpp
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
CLSID de l’objet à créer.

*riid*<br/>
IID de l’interface demandée.

*ppv*<br/>
Pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *PPV* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode est appelée par [CAtlDllModuleT ::D llgetclassobject](#dllgetclassobject) et est incluse pour la compatibilité descendante.

## <a name="see-also"></a>Voir aussi

[CAtlModuleT, classe](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT, classe](../../atl/reference/catlexemodulet-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
