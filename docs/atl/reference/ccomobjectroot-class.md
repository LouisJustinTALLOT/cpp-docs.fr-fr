---
title: CComObjectRoot, classe
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 9a9ffa1813fb15297d209894050b6bcce6802df2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298644"
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

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

## <a name="see-also"></a>Voir aussi

[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject, classe](../../atl/reference/ccompolyobject-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
