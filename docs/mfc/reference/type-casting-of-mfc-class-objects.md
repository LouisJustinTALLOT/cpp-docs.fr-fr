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
ms.openlocfilehash: c7586f3c3f3aefd78fa868cc847df27e8aac58ab
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611646"
---
# <a name="type-casting-of-mfc-class-objects"></a>Cast de type des objets de classe MFC

Macros de conversion de type permettent d’effectuer un cast de pointeur donné vers un pointeur qui pointe vers un objet de classe spécifique, avec ou sans vérifier que le cast est autorisé.

Le tableau suivant répertorie les macros de conversion de type MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Macros casté pointeurs vers des objets de classe MFC

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Convertit un pointeur vers un pointeur vers un objet de classe lors de la vérification pour voir si le cast est valide.|
|[STATIC_DOWNCAST](#static_downcast)|Convertit un pointeur vers un objet d’une classe à un pointeur d’un type connexe. Dans une version debug, provoque une assertion si l’objet n’est pas un « type de » le type de cible.|

##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST

Vous permet d’effectuer un cast d’un pointeur vers un pointeur vers un objet de classe lors de la vérification pour voir si le cast est valide.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Paramètres

*class*<br/>
Le nom d’une classe.

*pointer*<br/>
Un pointeur à être casté en un pointeur vers un objet de type *classe*.

### <a name="remarks"></a>Notes

La macro chargé de convertir le *pointeur* paramètre à un pointeur vers un objet de la *classe* type du paramètre.

Si l’objet référencé par le pointeur est un « type de » la classe identifiée, la macro retourne le pointeur approprié. Si elle n’est pas un cast légal, la macro retourne la valeur NULL.

##  <a name="static_downcast"></a>  STATIC_DOWNCAST

Les casts *pobject* vers un autre pointeur vers un *class_name* objet.

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe en cours de conversion.

*pobject*<br/>
Le pointeur à être casté en un pointeur vers un *class_name* objet.

### <a name="remarks"></a>Notes

*pObject* doit avoir la valeur NULL, soit pointer vers un objet d’une classe dérivée directement ou indirectement, à partir de *class_name*. Dans les versions de votre application avec le symbole de préprocesseur _DEBUG défini, la macro DÉCLARERA si *pobject* n’est pas NULL, ou s’il pointe vers un objet qui n’est pas un « type de » la classe spécifiée dans le *class_name*paramètre (voir [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). Non- **_DEBUG** builds, la macro effectue le cast sans vérification de type.

La classe spécifiée dans le *class_name* paramètre doit être dérivé `CObject` et doit utiliser le DECLARE_DYNAMIC et IMPLEMENT_DYNAMIC, macros DECLARE_DYNCREATE et IMPLEMENT_DYNCREATE, ou DECLARE_SERIAL et IMPLEMENT_ Macros de série comme expliqué dans l’article [classe CObject : Dérivation d’une classe de CObject](../../mfc/deriving-a-class-from-cobject.md).

Par exemple, vous pouvez caster un pointeur vers `CMyDoc`, appelé `pMyDoc`, vers un autre pointeur vers `CDocument` à l’aide de cette expression :

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Si `pMyDoc` ne pointe pas vers un objet dérivé directement ou indirectement de `CDocument`, la macro DÉCLARERA.

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
