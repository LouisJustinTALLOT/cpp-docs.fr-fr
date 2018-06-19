---
title: Classe de IEnumOnSTLImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
dev_langs:
- C++
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1de4bdd0d07e694303f850d6298d77afe3322214
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365254"
---
# <a name="ienumonstlimpl-class"></a>Classe de IEnumOnSTLImpl
Cette classe définit une interface d’énumérateur basée sur une collection de la bibliothèque C++ Standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```  
  
#### <a name="parameters"></a>Paramètres  
 `Base`  
 Un énumérateur COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interface.  
  
 `piid`  
 Pointeur vers l’ID de l’interface de l’énumérateur.  
  
 `T`  
 Le type d’élément exposé par l’interface de l’énumérateur.  
  
 `Copy`  
 A [copier la classe de stratégie](../../atl/atl-copy-policy-classes.md).  
  
 `CollType`  
 Une classe de conteneur de bibliothèque C++ Standard.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](#clone)|L’implémentation de [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx).|  
|[IEnumOnSTLImpl::Init](#init)|Initialise l’énumérateur.|  
|[IEnumOnSTLImpl::Next](#next)|L’implémentation de [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx).|  
|[IEnumOnSTLImpl::Reset](#reset)|L’implémentation de [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx).|  
|[IEnumOnSTLImpl::Skip](#skip)|L’implémentation de [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx).|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m_iter](#m_iter)|Itérateur qui représente la position actuelle de l’énumérateur dans la collection.|  
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Pointeur vers le conteneur de la bibliothèque Standard C++ contenant les éléments à énumérer.|  
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|Le **IUnknown** pointeur de l’objet en fournissant la collection.|  
  
## <a name="remarks"></a>Notes  
 `IEnumOnSTLImpl` fournit l’implémentation pour une interface d’énumérateur COM où les éléments en cours d’énumération sont stockées dans un conteneur de bibliothèque C++ Standard compatible. Cette classe est analogue à la [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) (classe), qui fournit une implémentation d’une interface d’énumérateur basé sur un tableau.  
  
> [!NOTE]
>  Consultez [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) pour plus d’informations sur les autres différences entre `CComEnumImpl` et `IEnumOnSTLImpl`.  
  
 En règle générale, vous allez *pas* permettant de créer votre propre classe de l’énumérateur en dérivant de cette implémentation de l’interface. Si vous souhaitez utiliser un énumérateur fourni par ATL basé sur un conteneur de bibliothèque C++ Standard, il est plus courant de créer une instance de [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), ou pour créer une classe de collection qui retourne un énumérateur en dérivant de [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).  
  
 Toutefois, si vous n’avez pas besoin de fournir un énumérateur personnalisé (par exemple, une qui expose des interfaces en plus de l’interface d’énumérateur), vous pouvez dériver de cette classe. Dans ce cas, il est probable que vous devez remplacer le [Clone](#clone) méthode pour fournir votre propre implémentation.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="init"></a>  IEnumOnSTLImpl::Init  
 Initialise l’énumérateur.  
  
```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```  
  
### <a name="parameters"></a>Paramètres  
 `pUnkForRelease`  
 [in] Le **IUnknown** pointeur d’un objet qui doit rester actif pendant la durée de vie de l’énumérateur. Passer **NULL** si aucun objet n’existe.  
  
 `collection`  
 Une référence au conteneur de bibliothèque C++ Standard qui contient les éléments à énumérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Si vous passez `Init` une référence à une collection contenues dans un autre objet, vous pouvez utiliser la `pUnkForRelease` paramètre pour vous assurer que l’objet et la collection, sa valeur est, est disponible pour tant que l’énumérateur a besoin.  
  
 Vous devez appeler cette méthode avant de passer un pointeur vers l’interface de l’énumérateur sur tous les clients.  
  
##  <a name="clone"></a>  IEnumOnSTLImpl::Clone  
 Cette méthode fournit l’implémentation de la [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx) méthode en créant un objet de type `CComEnumOnSTL`, l’initialise avec la même collection et itérateur utilisé par l’objet actuel et le renvoi de l’interface sur objet qui vient d’être créé.  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] L’interface de l’énumérateur sur un objet nouvellement créé cloné à partir de l’énumérateur en cours.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk  
 Le **IUnknown** pointeur de l’objet en fournissant la collection.  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
### <a name="remarks"></a>Notes  
 Ce pointeur intelligent conserve une référence sur l’objet passé à [IEnumOnSTLImpl::Init](#init), garantissant qu’il reste actif pendant la durée de vie de l’énumérateur.  
  
##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection  
 Ce membre pointe vers la collection qui fournit les données de la mise en place de l’interface de l’énumérateur.  
  
```
CollType* m_pcollection;
```  
  
### <a name="remarks"></a>Notes  
 Ce membre est initialisé par un appel à [IEnumOnSTLImpl::Init](#init).  
  
##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter  
 Ce membre contient l’itérateur utilisé pour marquer la position actuelle dans la collection et de parcourir les éléments suivants.  
  
```
CollType::iterator m_iter;
```  
  
##  <a name="next"></a>  IEnumOnSTLImpl::Next  
 Cette méthode fournit l’implémentation de la [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) (méthode).  
  
```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre d’éléments demandés.  
  
 `rgelt`  
 [out] Tableau à remplir avec les éléments.  
  
 `pceltFetched`  
 [out] Le nombre d’éléments réellement retournés dans `rgelt`. Cela peut être inférieur à `celt` si moins de `celt` éléments restant dans la liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="reset"></a>  IEnumOnSTLImpl::Reset  
 Cette méthode fournit l’implémentation de la [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx) (méthode).  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="skip"></a>  IEnumOnSTLImpl::Skip  
 Cette méthode fournit l’implémentation de la [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx) (méthode).  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre d’éléments à ignorer.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
