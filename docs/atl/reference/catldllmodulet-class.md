---
title: Classe CAtlDllModuleT
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
ms.openlocfilehash: 7a5f8e7e489c8e0d573569ac7c4a8fb63f652732
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319016"
---
# <a name="catldllmodulet-class"></a>Classe CAtlDllModuleT

Cette classe représente le module pour un DLL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe `CAtlDllModuleT`dérivée de .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtldllModuleT::CAtldllModuleT](#catldllmodulet)|Constructeur.|
|[CAtldllModuleT::CAtldllModuleT](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Testez si le DLL peut être déchargé.|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Retourne une usine de classe.|
|[CAtlDllModuleT::DllMain](#dllmain)|Le point d’entrée optionnel dans une bibliothèque à liaison dynamique (DLL).|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Ajoute des entrées au registre du système pour les objets dans le DLL.|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Supprime les entrées dans le registre du système pour les objets dans le DLL.|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Retourne une usine de classe. Invoqué par [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Notes

`CAtlDllModuleT`représente le module d’une bibliothèque à liaison dynamique (DLL) et fournit les fonctions utilisées par tous les projets DLL. Cette spécialisation de la classe [CAtlModuleT](../../atl/reference/catlmodulet-class.md) comprend le soutien à l’inscription.

Pour plus d’informations sur les modules dans ATL, voir [atL Module Classes](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CAtldllModuleT::CAtldllModuleT

Constructeur.

```
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtldllModuleT::CAtldllModuleT

Destructeur.

```
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow

Testez si le DLL peut être déchargé.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Valeur de retour

Les retours S_OK si le DLL peut être déchargé, ou S_FALSE s’il ne peut pas.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject

Retourne l’usine de classe.

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
Le CLSID de l’objet à créer.

*riid*<br/>
L’IID de l’interface demandée.

*Ppv*<br/>
Un pointeur au pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppv* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::DllMain

Le point d’entrée optionnel dans une bibliothèque à liaison dynamique (DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Paramètres

*dwReason*<br/>
Si elles sont définies pour DLL_PROCESS_ATTACH, les appels de notification DLL_THREAD_ATTACH et DLL_THREAD_DETACH sont désactivés.

*lpReserved*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne toujours VRAI.

### <a name="remarks"></a>Notes

Désactiver les appels de notification DLL_THREAD_ATTACH et DLL_THREAD_DETACH peut être une optimisation utile pour les applications multithreaded qui ont de nombreux DLL, qui créent et suppriment fréquemment des threads, et dont les DLL n’ont pas besoin de ces notifications de niveau de thread de pièce jointe / détachement.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer

Ajoute des entrées au registre du système pour les objets dans le DLL.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
VRAI si la bibliothèque de type doit être enregistrée. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer

Supprime les entrées dans le registre du système pour les objets dans le DLL.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
VRAI si la bibliothèque de type doit être retirée du registre. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT::GetClassObject

Crée un objet du CLSID spécifié.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
Le CLSID de l’objet à créer.

*riid*<br/>
L’IID de l’interface demandée.

*Ppv*<br/>
Un pointeur au pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppv* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode est appelée par [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) et est incluse pour la compatibilité vers l’arrière.

## <a name="see-also"></a>Voir aussi

[Classe CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Classe CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de modules](../../atl/atl-module-classes.md)
