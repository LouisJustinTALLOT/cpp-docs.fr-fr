---
title: Fonctions globales d’enregistrement des serveurs
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: fb6353b52f487d0511c54223fe9e31dab88704b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325931"
---
# <a name="server-registration-global-functions"></a>Fonctions globales d’enregistrement des serveurs

Ces fonctions fournissent un support pour l’enregistrement et l’enregistrement des objets serveur dans la carte de l’objet.

> [!IMPORTANT]
> Les fonctions énumérées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Cette fonction est appelée pour inscrire chaque objet du mappage d'objets.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Cette fonction est appelée pour annuler l'inscription de chaque objet du mappage d'objets.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Cette fonction est appelée pour inscrire des objets de classe.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Cette fonction est appelée à révoquer les objets de classe d’un module COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Cette fonction est appelée pour obtenir l’objet de classe.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a>AtlComModuleRéservateur

Cette fonction est appelée pour inscrire chaque objet du mappage d'objets.

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Paramètres

*pComModule*<br/>
Pointeur vers le module COM.

*bRegTypeLib*<br/>
VRAI si la bibliothèque de type doit être enregistrée.

*pCLSID (en)*<br/>
Indique le CLSID de l’objet à enregistrer. Si NULL, tous les objets de la carte de l’objet seront enregistrés.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

`AtlComModuleRegisterServer`parcourt la carte des objets autogénérés ATL et enregistre chaque objet dans la carte. Si *le pCLSID* n’est pas NULL, alors seul l’objet mentionné par *pCLSID* est enregistré; sinon tous les objets sont enregistrés.

Cette fonction est appelée par [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer

Cette fonction est appelée pour annuler l'inscription de chaque objet du mappage d'objets.

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Paramètres

*pComModule*<br/>
Pointeur vers le module COM.

*bUnRegTypeLib*<br/>
VRAI si la bibliothèque de type doit être enregistrée.

*pCLSID (en)*<br/>
Indique que le CLSID de l’objet n’est pas enregistré. Si NULL tous les objets de la carte de l’objet ne seront pas enregistrés.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

`AtlComModuleUnregisterServer`marche sur la carte des objets ATL et ne répercrit pas chaque objet sur la carte. Si *le pCLSID* n’est pas NULL, alors seul l’objet mentionné par *pCLSID* n’est pas enregistré; sinon tous les objets ne sont pas enregistrés.

Cette fonction est appelée par [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects

Cette fonction est appelée pour inscrire des objets de classe.

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*pComModule*<br/>
Pointeur vers le module COM.

*dwClsContexte*<br/>
Spécifie le contexte dans lequel l’objet de classe doit être exécuté. Les valeurs possibles sont CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER ou CLSCTX_LOCAL_SERVER. Voir [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) pour plus de détails.

*dwFlags*<br/>
Détermine les types de connexion à l’objet de classe. Les valeurs possibles sont REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE ou REGCLS_MULTI_SEPARATE. Voir [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) pour plus de détails.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction d’aide est utilisée par [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (obsolète en ATL 7.0) et [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects

Cette fonction est appelée pour supprimer la ou les fabriques de classes de la table des objets en cours d'exécution (ROT).

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Paramètres

*pComModule*<br/>
Pointeur vers le module COM.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction d’aide est utilisée par [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (obsolète en ATL 7.0) et [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject

Cette fonction est appelée pour retourner la fabrique de classe.

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>Paramètres

*pComModule*<br/>
Pointeur vers le module COM.

*rclsid*<br/>
Le CLSID de l’objet à créer.

*riid*<br/>
L’IID de l’interface demandée.

*Ppv*<br/>
Un pointeur au pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppv* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction d’aide est utilisée par [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (obsolète en ATL 7.0) et [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
