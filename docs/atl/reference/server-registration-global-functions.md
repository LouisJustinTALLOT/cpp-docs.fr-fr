---
title: Fonctions globales d’inscription de serveur
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: f9c3697259e1cee2b1107ded785ca583d730b55e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495461"
---
# <a name="server-registration-global-functions"></a>Fonctions globales d’inscription de serveur

Ces fonctions assurent la prise en charge de l’inscription et de l’annulation de l’inscription des objets serveur dans le mappage d’objets.

> [!IMPORTANT]
>  Les fonctions listées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Cette fonction est appelée pour inscrire chaque objet du mappage d'objets.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Cette fonction est appelée pour annuler l'inscription de chaque objet du mappage d'objets.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Cette fonction est appelée pour inscrire des objets de classe.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Cette fonction est appelée pour révoquer des objets de classe d’un module COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Cette fonction est appelée pour récupérer l’objet de classe.|

## <a name="requirements"></a>Configuration requise

**En-tête:** atlbase. h

##  <a name="atlcommoduleregisterserver"></a>  AtlComModuleRegisterServer

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
TRUE si la bibliothèque de types doit être inscrite.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet à inscrire. Si la valeur est NULL, tous les objets de la table de mappage d’objets seront inscrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`AtlComModuleRegisterServer`parcourt le mappage d’objets générés automatiquement par ATL et inscrit chaque objet dans le mappage. Si *pCLSID* n’a pas la valeur null, seul l’objet référencé par *pCLSID* est inscrit; Sinon, tous les objets sont inscrits.

Cette fonction est appelée par [CAtlComModule:: RegisterServer](catlcommodule-class.md#registerserver).

##  <a name="atlcommoduleunregisterserver"></a>  AtlComModuleUnregisterServer

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
TRUE si la bibliothèque de types doit être inscrite.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet dont l’inscription doit être annulée. Si la valeur NULL, tous les objets dans le mappage d’objets seront désinscrits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`AtlComModuleUnregisterServer`parcourt le mappage d’objet ATL et annule l’inscription de chaque objet dans la classe Map. Si *pCLSID* n’a pas la valeur null, seul l’enregistrement de l’objet référencé par *pCLSID* est annulé; dans le cas contraire, tous les objets sont désinscrits.

Cette fonction est appelée par [CAtlComModule:: UnregisterServer](catlcommodule-class.md#unregisterserver).

##  <a name="atlcommoduleregisterclassobjects"></a>  AtlComModuleRegisterClassObjects

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

*dwClsContext*<br/>
Spécifie le contexte dans lequel l’objet de classe doit être exécuté. Les valeurs possibles sont CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER ou CLSCTX_LOCAL_SERVER. Pour plus d’informations, consultez [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) .

*dwFlags*<br/>
Détermine les types de connexion à l’objet de classe. Les valeurs possibles sont REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE ou REGCLS_MULTI_SEPARATE. Pour plus d’informations, consultez [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) .

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction d’assistance est utilisée par [CComModule:: RegisterClassObjects](ccommodule-class.md#registerclassobjects) (obsolète dans ATL 7,0) et [CAtlExeModuleT:: RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

##  <a name="atlcommodulerevokeclassobjects"></a>  AtlComModuleRevokeClassObjects

Cette fonction est appelée pour supprimer la ou les fabriques de classes de la table des objets en cours d'exécution (ROT).

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Paramètres

*pComModule*<br/>
Pointeur vers le module COM.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction d’assistance est utilisée par [CComModule:: RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (obsolète dans ATL 7,0) et [CAtlExeModuleT:: RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

##  <a name="atlcommodulegetclassobject"></a>  AtlComModuleGetClassObject

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
CLSID de l’objet à créer.

*riid*<br/>
IID de l’interface demandée.

*ppv*<br/>
Pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *PPV* a la valeur null.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction d’assistance est utilisée par [CComModule:: GetClassObject,](ccommodule-class.md#getclassobject) (obsolète dans ATL 7,0) et [CAtlDllModuleT:: GetClassObject,](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
