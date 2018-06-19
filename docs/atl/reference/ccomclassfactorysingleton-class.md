---
title: Classe de CComClassFactorySingleton | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 754a3abd02a4a09df3e36aa9aea75c400ef00761
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360379"
---
# <a name="ccomclassfactorysingleton-class"></a>Classe de CComClassFactorySingleton
Cette classe dérive [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique.  
  
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
  
 `CComClassFactorySingleton` dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique. Chaque appel à la `CreateInstance` méthode interroge simplement cet objet pour un pointeur d’interface.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Requêtes `m_spObj` pour un pointeur d’interface.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComClassFactorySingleton::m_spObj](#m_spobj)|Le [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objet construit par `CComClassFactorySingleton`.|  
  
## <a name="remarks"></a>Notes  
 Objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe inclut la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare `CComClassFactory` en tant que la fabrique de classe par défaut. Pour utiliser `CComClassFactorySingleton`, spécifiez la [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) macro dans la définition de classe de votre objet. Par exemple :  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactorySingleton::CreateInstance  
 Appels `QueryInterface` via [m_spObj](#m_spobj) pour récupérer un pointeur d’interface.  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>Paramètres  
 `pUnkOuter`  
 [in] Si l’objet est créé dans le cadre d’un agrégat, puis `pUnkOuter` doit être inconnu externe. Dans le cas contraire, `pUnkOuter` doit être **NULL**.  
  
 `riid`  
 [in] IID de l’interface demandée. Si `pUnkOuter` est non - **NULL**, `riid` doit être **IID_IUnknown**.  
  
 `ppvObj`  
 [out] Un pointeur vers le pointeur d’interface identifié par `riid`. Si l’objet ne prend pas en charge cette interface, `ppvObj` a la valeur **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj  
 Le [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objet construit par `CComClassFactorySingleton`.  
  
```
CComPtr<IUnknown> m_spObj;
```  
  
### <a name="remarks"></a>Notes  
 Chaque appel à la [CreateInstance](#createinstance) méthode interroge simplement cet objet pour un pointeur d’interface.  
  
 Notez que le formulaire actuel de `m_spObj` présente une modification avec rupture de la manière qui `CComClassFactorySingleton` fonctionnait dans les versions précédentes d’ATL. Dans les versions précédentes du `CComClassFactorySingleton` objet a été créé en même temps que la fabrique de classe, lors de l’initialisation du serveur. Dans Visual C++ .NET 2003, l’objet est créé de manière différée, à la première demande. Cette modification peut provoquer des erreurs dans les programmes qui s’appuient sur l’initialisation anticipée.  
  
## <a name="see-also"></a>Voir aussi  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [Classe de CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)   
 [Classe de CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
