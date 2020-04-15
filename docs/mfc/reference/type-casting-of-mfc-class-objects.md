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
ms.openlocfilehash: 953acc32c3510b31c265f2d64d0a013f6dee06cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372893"
---
# <a name="type-casting-of-mfc-class-objects"></a>Cast de type des objets de classe MFC

Les macros de coulée de type fournissent un moyen de jeter un pointeur donné à un pointeur qui pointe vers un objet de classe spécifique, avec ou sans vérifier que le casting est légal.

Le tableau suivant répertorie les macros de coulée de type MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Macros qui jettent des pointeurs aux objets de classe MFC

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Lance un pointeur à un pointeur à un objet de classe tout en vérifiant si le casting est légal.|
|[STATIC_DOWNCAST](#static_downcast)|Lance un pointeur à un objet d’une classe à un pointeur d’un type connexe. Dans une construction de débaillement, provoque un ASSERT si l’objet n’est pas un "type" du type cible.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST

Fournit un moyen pratique de jeter un pointeur à un pointeur à un objet de classe tout en vérifiant si le casting est légal.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Paramètres

*class*<br/>
Nom d'une classe.

*pointeur*<br/>
Un pointeur à jeter à un pointeur à un objet de *classe*de type .

### <a name="remarks"></a>Notes

La macro jettera le *paramètre de pointeur* à un pointeur à un objet du type de paramètre de *classe.*

Si l’objet référencé par le pointeur est une «sorte de» la classe identifiée, la macro renvoie le pointeur approprié. S’il ne s’agit pas d’un casting juridique, la macro retourne NULL.

## <a name="static_downcast"></a><a name="static_downcast"></a>STATIC_DOWNCAST

Lance *pobject* à un pointeur à un *objet class_name.*

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe étant jeté à.

*pobject*<br/>
Le pointeur à jeter à un pointeur à un *objet class_name.*

### <a name="remarks"></a>Notes

*pobject* doit soit être NULL, soit pointer vers un objet d’une classe qui est dérivé directement, ou indirectement, de *class_name*. Dans les builds de votre application avec le symbole _DEBUG préprocesseur défini, la macro assert si *pobject* n’est pas NULL, ou si elle pointe vers un objet qui n’est pas un "type de" la classe spécifiée dans le *paramètre class_name* (voir [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). Dans les constructions non **_DEBUG,** la macro effectue le casting sans aucune vérification de type.

La classe spécifiée dans *le* class_name paramètre doit être dérivée `CObject` et doit utiliser le DECLARE_DYNAMIC et IMPLEMENT_DYNAMIC, le DECLARE_DYNCREATE et le IMPLEMENT_DYNCREATE, ou les macros DECLARE_SERIAL et IMPLEMENT_SERIAL comme expliqué dans l’article [CObject Class: Deriving a Class from CObject](../../mfc/deriving-a-class-from-cobject.md).

Par exemple, vous pouvez `CMyDoc`lancer `pMyDoc`un pointeur `CDocument` à , appelé , à un pointeur à l’aide de cette expression:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Si `pMyDoc` ne pointe pas un objet dérivé `CDocument`directement ou indirectement de , la macro assert.

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
