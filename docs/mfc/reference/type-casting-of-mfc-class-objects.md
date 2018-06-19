---
title: Type de conversion d’objets de classe MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 217be53a78a65a0f617438127b922b20c950853d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371158"
---
# <a name="type-casting-of-mfc-class-objects"></a>Cast de type des objets de classe MFC
Macros de conversion de type permettent d’effectuer un cast d’un pointeur spécifié vers un pointeur qui pointe vers un objet de classe spécifique, avec ou sans vérifier que le cast est autorisé.  
  
 Le tableau suivant répertorie les macros de conversion de type MFC.  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Macros casté pointeurs vers les objets de classe MFC  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Convertit un pointeur vers un pointeur vers un objet de classe lors de la vérification pour voir si le cast est valide.|  
|[STATIC_DOWNCAST](#static_downcast)|Convertit un pointeur vers un objet d’une classe à un pointeur d’un type connexe. Dans une version debug, entraîne un **ASSERT** si l’objet n’est pas un « type de » le type de cible.|  
  
##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST  
 Offre un moyen pratique d’effectuer un cast d’un pointeur vers un pointeur vers un objet de classe lors de la vérification pour voir si le cast est valide.  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>Paramètres  
 `class`  
 Le nom d’une classe.  
  
 `pointer`  
 Un pointeur pour être converti en un pointeur vers un objet de type `class`.  
  
### <a name="remarks"></a>Notes  
 La macro sera effectué le `pointer` paramètre en un pointeur vers un objet de la `class` type du paramètre.  
  
 Si l’objet référencé par le pointeur est un « type de » la classe identifiée, la macro retourne le pointeur approprié. Si elle n’est pas une conversion valides, la macro retourne **NULL**.  
  
##  <a name="static_downcast"></a>  STATIC_DOWNCAST  
 Les casts *pobject* vers un pointeur vers un *class_name* objet.  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe en cours de conversion.  
  
 *pObject*  
 Le pointeur d’être converti en un pointeur vers un *class_name* objet.  
  
### <a name="remarks"></a>Notes  
 *pObject* doit être **NULL**, ou pointer vers un objet d’une classe qui est dérivée directement ou indirectement, à partir de *class_name*. Dans les versions de votre application avec le **_DEBUG** sera de symbole de préprocesseur défini, la macro **ASSERT** si *pobject* n’est pas **NULL**, ou s’il pointe vers un objet qui n’est pas un « type de » de la classe spécifiée dans le *class_name* paramètre (voir [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). Non- **_DEBUG** builds, la macro effectue la conversion en sans vérification de type.  
  
 La classe spécifiée dans le *class_name* paramètre doit être dérivé `CObject` et doivent utiliser le `DECLARE_DYNAMIC` et `IMPLEMENT_DYNAMIC`, le `DECLARE_DYNCREATE` et `IMPLEMENT_DYNCREATE`, ou `DECLARE_SERIAL` et `IMPLEMENT_SERIAL`macros comme expliqué dans l’article [classe CObject : dérivation d’une classe de CObject](../../mfc/deriving-a-class-from-cobject.md).  
  
 Par exemple, vous pouvez caster un pointeur vers `CMyDoc`, appelé `pMyDoc`, vers un pointeur vers **CDocument** à l’aide de cette expression :  
  
 [!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 Si `pMyDoc` ne pointe pas vers un objet dérivé directement ou indirectement de **CDocument**, la macro sera **ASSERT**.  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
