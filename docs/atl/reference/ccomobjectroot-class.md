---
title: CComObjectRoot, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2832b9866145d9af510302c8c6d327972205495
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38952966"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot, classe
Ce typedef de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) est mise en modèle sur la valeur par défaut, le modèle du serveur de thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```  
  
## <a name="remarks"></a>Notes  
 `CComObjectRoot` est un `typedef` de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) transformer en modèle sur la valeur par défaut, le modèle du serveur de thread. Par conséquent [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) soit référencera [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).  
  
 `CComObjectRootEx` gère la gestion du nombre de référence objet pour les objets non regroupées en agrégats et agrégées. Elle contient le nombre de références d’objet si votre objet n’est pas agrégée et conserve le pointeur vers l’inconnu externe si votre objet est en cours d’agrégation. Pour les objets agrégées, `CComObjectRootEx` méthodes peuvent être utilisées pour gérer l’échec de l’objet interne pour construire et à protéger l’objet externe à partir de suppression lors de la publication des interfaces internes ou l’objet interne est supprimé.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
## <a name="see-also"></a>Voir aussi  
 [CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)   
 [CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)   
 [CComObject, classe](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject, classe](../../atl/reference/ccompolyobject-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
