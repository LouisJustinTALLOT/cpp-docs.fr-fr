---
title: Classe de CComEnumOnSTL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs:
- C++
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c380ba7b6c2c13f178a15263e1ff510f9f3c31c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363296"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL (classe)
Cette classe définit un objet d’énumérateur COM basé sur une collection de la bibliothèque C++ Standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>  
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
 T,
    Copy,
 CollType>,
    public CComObjectRootEx<ThreadModel>
```  
  
#### <a name="parameters"></a>Paramètres  
 `Base`  
 Un énumérateur COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interface.  
  
 `piid`  
 Pointeur vers l’ID de l’interface de l’énumérateur.  
  
 `T`  
 Le type d’élément exposé par l’interface de l’énumérateur.  
  
 `Copy`  
 A [Copier stratégie](../../atl/atl-copy-policy-classes.md) classe.  
  
 `CollType`  
 Une classe de conteneur de bibliothèque C++ Standard.  
  
## <a name="remarks"></a>Notes  
 `CComEnumOnSTL` définit un objet d’énumérateur COM basé sur une collection de la bibliothèque C++ Standard. Cette classe peut être utilisée sur sa propre ou en association avec [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Procédure standard d’utilisation de cette classe est décrites ci-dessous. Pour plus d’informations, consultez [Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Pour utiliser cette classe avec ICollectionOnSTLImpl :  
  
- `typedef` une spécialisation de cette classe.  
  
-   Utilisez le `typedef` comme argument template final dans une spécialisation de `ICollectionOnSTLImpl`.  
  
 Consultez [Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md) pour obtenir un exemple.  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Pour utiliser cette classe indépendamment ICollectionOnSTLImpl :  
  
- `typedef` une spécialisation de cette classe.  
  
-   Utilisez le `typedef` comme argument template dans une spécialisation de `CComObject`.  
  
-   Créez une instance de la `CComObject` spécialisation.  
  
-   Initialiser l’objet énumérateur en appelant [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).  
  
-   Retourne l’interface de l’énumérateur au client.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous fournit une fonction générique pour gérer la création et l’initialisation d’un objet énumérateur :  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 Cette fonction de modèle peut être utilisée pour implémenter le `_NewEnum` propriété d’une interface de collection, comme indiqué ci-dessous :  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 Ce code crée un `typedef` pour `CComEnumOnSTL` qui expose un vecteur de `CComVariant`s à l’aide de la **IEnumVariant** interface. Le **CVariantCollection** classe spécialisée simplement **CreateSTLEnumerator** pour travailler avec des objets de ce type d’énumérateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [ATLCollections : Illustration ICollectionOnSTLImpl, CComEnumOnSTL et des Classes de stratégie de copie personnalisée](../../visual-cpp-samples.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [IEnumOnSTLImpl, classe](../../atl/reference/ienumonstlimpl-class.md)
