---
title: Fonctions globales de serveur d’inscription | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
dev_langs:
- C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fb3febbbaffc7c3a0de945fc9d30b544fd22188
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023304"
---
# <a name="server-registration-global-functions"></a>Fonctions globales de serveur d’inscription

Ces fonctions fournissent la prise en charge pour inscrire et désinscrire des objets de serveur du mappage d’objets.

> [!IMPORTANT]
>  Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Cette fonction est appelée pour inscrire chaque objet du mappage d'objets.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Cette fonction est appelée pour annuler l'inscription de chaque objet du mappage d'objets.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Cette fonction est appelée pour inscrire des objets de classe.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Cette fonction est appelée pour révoquer des objets de classe à partir d’un module COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Cette fonction est appelée pour obtenir l’objet de classe.|  

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

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
TRUE si la bibliothèque de types doit être enregistré.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet à inscrire. Si NULL, tous les objets du mappage d’objets seront inscrit.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`AtlComModuleRegisterServer` Décrit le mappage d’objets ATL généré automatiquement et inscrit chaque objet dans le mappage. Si *pCLSID* n’est pas NULL, alors seulement l’objet référencé par *pCLSID* est inscrite ; sinon, tous les objets sont enregistrés.

Cette fonction est appelée par [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).

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
TRUE si la bibliothèque de types doit être enregistré.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet doit être annulée. Si NULL, tous les objets du mappage d’objets sera annulées.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

`AtlComModuleUnregisterServer` Décrit le mappage d’objets ATL et annule l’inscription de chaque objet dans le mappage. Si *pCLSID* n’est pas NULL, alors seulement l’objet référencé par *pCLSID* est désinscrite ; sinon tous les objets sont annulées.

Cette fonction est appelée par [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).

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
Spécifie le contexte dans lequel l’objet de classe doit être exécuté. Les valeurs possibles sont CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER ou CLSCTX_LOCAL_SERVER. Consultez [CLSCTX](https://msdn.microsoft.com/library/windows/desktop/ms693716) pour plus d’informations.

*dwFlags*<br/>
Détermine les types de connexion à l’objet de classe. Les valeurs possibles sont REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE ou REGCLS_MULTI_SEPARATE. Consultez [REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls) pour plus d’informations.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction d’assistance utilisée par [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (déconseillé dans ATL 7.0) et [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

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

Cette fonction d’assistance utilisée par [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (déconseillé dans ATL 7.0) et [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

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
Le CLSID de l’objet doit être créé.

*riid*<br/>
IID de l’interface demandée.

*PPV*<br/>
Un pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppv* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction d’assistance utilisée par [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (déconseillé dans ATL 7.0) et [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
