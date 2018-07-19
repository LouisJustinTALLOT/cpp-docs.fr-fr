---
title: CComEnumOnSTL, classe | Microsoft Docs
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
ms.openlocfilehash: ca7b7d38c204d7dd8402b9d610a5800dcef6ced9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883227"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL, classe
Cette classe définit un objet d’énumérateur COM selon une collection de la bibliothèque C++ Standard.  
  
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
 *base de*  
 Un énumérateur COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interface.  
  
 *piid*  
 Pointeur vers l’ID d’interface de l’interface de l’énumérateur.  
  
 *T*  
 Le type d’élément exposé par l’interface de l’énumérateur.  
  
 *Copier*  
 Un [Copier stratégie](../../atl/atl-copy-policy-classes.md) classe.  
  
 *CollType*  
 Une classe de conteneur de bibliothèque C++ Standard.  
  
## <a name="remarks"></a>Notes  
 `CComEnumOnSTL` définit un objet d’énumérateur COM selon une collection de la bibliothèque C++ Standard. Cette classe peut être utilisée sur sa propre ou conjointement avec [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Procédure standard d’utilisation de cette classe est décrites ci-dessous. Pour plus d’informations, consultez [Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Pour utiliser cette classe avec ICollectionOnSTLImpl :  
  
- **typedef** une spécialisation de cette classe.  
  
-   Utilisez le **typedef** en tant que l’argument template final dans une spécialisation de `ICollectionOnSTLImpl`.  
  
 Consultez [Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md) pour obtenir un exemple.  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Pour utiliser cette classe indépendamment ICollectionOnSTLImpl :  
  
- **typedef** une spécialisation de cette classe.  
  
-   Utilisez le **typedef** comme argument de modèle dans une spécialisation de `CComObject`.  
  
-   Créez une instance de la `CComObject` spécialisation.  
  
-   Initialiser l’objet énumérateur en appelant [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).  
  
-   Retourner l’interface de l’énumérateur au client.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
## <a name="example"></a>Exemple  
 Le code ci-dessous fournit une fonction pour gérer la création et l’initialisation d’un objet énumérateur générique :  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 Cette fonction de modèle peut être utilisée pour implémenter le `_NewEnum` propriété d’une interface de collection, comme indiqué ci-dessous :  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 Ce code crée un **typedef** pour `CComEnumOnSTL` qui expose un vecteur de `CComVariant`s au moyen de la `IEnumVariant` interface. Le `CVariantCollection` classe spécialisée simplement `CreateSTLEnumerator` pour travailler avec des objets d’énumérateur de ce type.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [ATLCollections : Illustration ICollectionOnSTLImpl, CComEnumOnSTL et des Classes de stratégie de copie personnalisées](../../visual-cpp-samples.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [IEnumOnSTLImpl, classe](../../atl/reference/ienumonstlimpl-class.md)
