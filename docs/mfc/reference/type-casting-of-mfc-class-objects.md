---
title: Cast de type des objets de classe MFC
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: e3702ced83021e42ac6bf71a78efc51fa07b8be9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840490"
---
# <a name="type-casting-of-mfc-class-objects"></a>Cast de type des objets de classe MFC

Les macros de conversion de type offrent un moyen d’effectuer un cast d’un pointeur donné vers un pointeur qui pointe vers un objet de classe spécifique, avec ou sans vérifier que le cast est légal.

Le tableau suivant répertorie les macros de conversion de type MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Macros qui effectuent un cast de pointeurs vers des objets de classe MFC

|Nom|Description|
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Effectue un cast d’un pointeur vers un pointeur vers un objet de classe tout en vérifiant si le cast est légal.|
|[STATIC_DOWNCAST](#static_downcast)|Effectue un cast d’un pointeur vers un objet d’une classe vers un pointeur d’un type connexe. Dans une version Debug, provoque une assertion si l’objet n’est pas un « genre » du type cible.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a> DYNAMIC_DOWNCAST

Offre un moyen pratique d’effectuer un cast d’un pointeur vers un pointeur vers un objet de classe tout en vérifiant si le cast est légal.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Paramètres

*class*<br/>
Nom d'une classe.

*dirigé*<br/>
Pointeur à convertir en pointeur vers un objet de *classe*de type.

### <a name="remarks"></a>Notes

La macro effectue un cast du paramètre de *pointeur* en un pointeur vers un objet du type du paramètre de *classe* .

Si l’objet référencé par le pointeur est un « genre » de la classe identifiée, la macro retourne le pointeur approprié. S’il ne s’agit pas d’une conversion légale, la macro retourne NULL.

## <a name="static_downcast"></a><a name="static_downcast"></a> STATIC_DOWNCAST

Convertit *pObject* en un pointeur vers un objet *class_name* .

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe vers laquelle effectuer un cast.

*pObject*<br/>
Pointeur à convertir en pointeur vers un objet *class_name* .

### <a name="remarks"></a>Notes

*pObject* doit avoir la valeur null, ou pointer vers un objet d’une classe qui est dérivée directement, ou indirectement, de *class_name*. Dans les builds de votre application avec le symbole de préprocesseur _DEBUG défini, la macro déclare si *pObject* n’a pas la valeur null, ou si elle pointe vers un objet qui n’est pas un « genre » de la classe spécifiée dans le paramètre *Class_name* (consultez [CObject :: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). Dans les builds non- **_DEBUG** , la macro effectue le cast sans vérification de type.

La classe spécifiée dans le paramètre *class_name* doit être dérivée de `CObject` et doit utiliser les DECLARE_DYNAMIC et IMPLEMENT_DYNAMIC, le DECLARE_DYNCREATE et le IMPLEMENT_DYNCREATE, ou les macros DECLARE_SERIAL et IMPLEMENT_SERIAL comme expliqué dans l’article [CObject, classe : dérivation d’une classe à partir de CObject](../../mfc/deriving-a-class-from-cobject.md).

Par exemple, vous pouvez effectuer un cast d’un pointeur vers `CMyDoc` , appelé `pMyDoc` , en pointeur vers à `CDocument` l’aide de cette expression :

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Si `pMyDoc` ne pointe pas vers un objet dérivé directement ou indirectement de `CDocument` , la macro fait l’objet d’une assertion.

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
