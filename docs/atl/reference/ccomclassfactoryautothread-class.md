---
title: Ccomclassfactoryautothread, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbd258761bef7789e73fe61ac288b414902d2af8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214072"
---
# <a name="ccomclassfactoryautothread-class"></a>Ccomclassfactoryautothread, classe
Cette classe implémente le [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interface et permet aux objets d’être créé dans plusieurs des cloisonnements.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComClassFactoryAutoThread 
   : public IClassFactory, 
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Crée un objet du CLSID spécifié.|  
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Verrouille la fabrique de classe en mémoire.|  
  
## <a name="remarks"></a>Notes  
 `CComClassFactoryAutoThread` est similaire à [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), mais permet aux objets d’être créé dans plusieurs des cloisonnements. Pour tirer parti de cette prise en charge, dérivez votre module EXE à partir de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe inclut la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) en tant que la fabrique de classe par défaut. Pour utiliser `CComClassFactoryAutoThread`, spécifiez la [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) macro dans la définition de classe de votre objet. Exemple :  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactoryAutoThread::CreateInstance  
 Crée un objet du CLSID spécifié et récupère un pointeur d’interface vers cet objet.  
  
```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnkOuter*  
 [in] Si l’objet est créé dans le cadre d’un agrégat, puis *pUnkOuter* doit être inconnu externe. Sinon, *pUnkOuter* doit être NULL.  
  
 *riid*  
 [in] IID de l’interface demandée. Si *pUnkOuter* n’est pas NULL, *riid* doit être `IID_IUnknown`.  
  
 *ppvObj*  
 [out] Un pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* est définie sur NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Si votre module dérive [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` sélectionne tout d’abord un thread pour créer l’objet dans le compartiment associé.  
  
##  <a name="lockserver"></a>  CComClassFactoryAutoThread::LockServer  
 Incrémente et décrémente le module nombre de verrous en appelant `_Module::Lock` et `_Module::Unlock`, respectivement.  
  
```
STDMETHODIMP LockServer(BOOL fLock);
```  
  
### <a name="parameters"></a>Paramètres  
 *Troupeau*  
 [in] Si la valeur est TRUE, le nombre de verrous est incrémenté ; Sinon, le nombre de verrous est décrémenté.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous utilisez `CComClassFactoryAutoThread`, `_Module` fait généralement référence à l’instance globale de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Appel `LockServer` permet à un client à maintenir une fabrique de classe afin que plusieurs objets peuvent être créés rapidement.  
  
## <a name="see-also"></a>Voir aussi  
 [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)   
 [CComClassFactory2, classe](../../atl/reference/ccomclassfactory2-class.md)   
 [Ccomclassfactorysingleton, classe](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
