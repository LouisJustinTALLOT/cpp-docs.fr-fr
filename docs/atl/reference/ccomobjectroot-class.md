---
description: 'En savoir plus sur : classe CComObjectRoot'
title: CComObjectRoot, classe
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 924b85ee7ed6e17eb44e753ad16f57251bb189ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142465"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot, classe

Ce typedef de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) est mis en modèle sur le modèle de thread par défaut du serveur.

## <a name="syntax"></a>Syntaxe

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>Notes

`CComObjectRoot` est un **`typedef`** de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) mis en modèle sur le modèle de thread par défaut du serveur. Par conséquent, [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) référence [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).

`CComObjectRootEx` gère la gestion du nombre de références d’objet pour les objets non agrégés et agrégés. Il contient le nombre de références de l’objet si votre objet n’est pas agrégé et contient le pointeur vers le externe inconnu si votre objet est en cours d’agrégation. Pour les objets agrégés, les `CComObjectRootEx` méthodes peuvent être utilisées pour gérer l’échec de la construction de l’objet interne et protéger l’objet externe lors de la libération des interfaces internes ou de la suppression de l’objet interne.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="see-also"></a>Voir aussi

[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject, classe](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject, classe](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject (classe)](../../atl/reference/ccompolyobject-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
