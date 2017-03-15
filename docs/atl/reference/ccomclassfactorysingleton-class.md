---
title: Classe de CComClassFactorySingleton | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComClassFactorySingleton
- ATL.CComClassFactorySingleton<T>
- ATL::CComClassFactorySingleton
- ATL::CComClassFactorySingleton<T>
- CComClassFactorySingleton
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 7ff6f3a9d00c0f579077d9502aefad5cbea35f17
ms.lasthandoff: 02/24/2017

---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton (classe)
Cette classe dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class CComClassFactorySingleton : public CComClassFactory
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe.  
  
 `CComClassFactorySingleton`dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique. Chaque appel à la `CreateInstance` méthode interroge simplement un pointeur d’interface de cet objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Requêtes `m_spObj` pour un pointeur d’interface.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComClassFactorySingleton::m_spObj](#m_spobj)|Le [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objet construit par `CComClassFactorySingleton`.|  
  
## <a name="remarks"></a>Remarques  
 Objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe inclut la macro [DECLARE_CLASSFACTORY](http://msdn.microsoft.com/library/51a6b925-07c0-4d3a-9174-0b8c808975e4), qui déclare `CComClassFactory` en tant que la fabrique de classe par défaut. Pour utiliser `CComClassFactorySingleton`, spécifiez la [DECLARE_CLASSFACTORY_SINGLETON](http://msdn.microsoft.com/library/0e4a3964-c03d-463e-884c-fe3b416db478) macro dans la définition de classe de votre objet. Exemple :  
  
 [!code-cpp[NVC_ATL_COM&#10;](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="a-namecreateinstancea--ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClassFactorySingleton::CreateInstance  
 Appels `QueryInterface` via [m_spObj](#m_spobj) pour récupérer un pointeur d’interface.  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>Paramètres  
 `pUnkOuter`  
 [in] Si l’objet est créé dans le cadre d’un agrégat, puis `pUnkOuter` doit être inconnu externe. Dans le cas contraire, `pUnkOuter` doit être **NULL**.  
  
 `riid`  
 [in] L’IID de l’interface demandée. Si `pUnkOuter` est non - **NULL**, `riid` doit être **IID_IUnknown**.  
  
 `ppvObj`  
 [out] Un pointeur vers le pointeur d’interface identifié par `riid`. Si l’objet ne prend pas en charge cette interface, `ppvObj` a **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="a-namemspobja--ccomclassfactorysingletonmspobj"></a><a name="m_spobj"></a>CComClassFactorySingleton::m_spObj  
 Le [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objet construit par `CComClassFactorySingleton`.  
  
```
CComPtr<IUnknown> m_spObj;
```  
  
### <a name="remarks"></a>Remarques  
 Chaque appel à la [CreateInstance](#createinstance) méthode interroge simplement un pointeur d’interface de cet objet.  
  
 Notez que le formulaire en cours de `m_spObj` présente une modification avec rupture de la manière qui `CComClassFactorySingleton` fonctionnait dans les versions précédentes d’ATL. Dans les versions précédentes du `CComClassFactorySingleton` objet a été créé en même temps que la fabrique de classe, pendant l’initialisation du serveur. Dans Visual C++ .NET 2003, l’objet est créé de manière différée, à la première demande. Cette modification peut provoquer des erreurs dans les programmes qui s’appuient sur l’initialisation anticipée.  
  
## <a name="see-also"></a>Voir aussi  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 (classe)](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactoryAutoThread (classe)](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

