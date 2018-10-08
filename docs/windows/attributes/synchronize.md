---
title: synchroniser (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.synchronize
dev_langs:
- C++
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 740d99bfbc0da4c290a09a95f5d4f8f227a11fc8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790713"
---
# <a name="synchronize"></a>synchronize

Synchronise l’accès à la méthode cible.

## <a name="syntax"></a>Syntaxe

```cpp
[synchronize]
```

## <a name="remarks"></a>Notes

Le **synchroniser** attribut C++ implémente la prise en charge pour la synchronisation de la méthode cible d’un objet. La synchronisation permet plusieurs objets à utiliser une ressource commune (par exemple, une méthode d’une classe) en contrôlant l’accès de la méthode cible.

Le code inséré par cet attribut appelle la bonne `Lock` (méthode) (déterminé par le modèle de thread) au début de la méthode cible. Lorsque la méthode est fermée, `Unlock` est appelée automatiquement. Pour plus d’informations sur ces fonctions, consultez [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

Cet attribut exige que le [coclasse](coclass.md), [progid](progid.md), ou [vi_progid](vi-progid.md) attribut (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliquée, `vi_progid` et `coclass` sont également appliquées.

## <a name="example"></a>Exemple

Le code suivant fournit la synchronisation pour le `UpdateBalance` méthode de la `CMyClass` objet.

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")  
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode de classe, méthode|
|**Renouvelable**|Non|
|**Attributs requis**|Un ou plusieurs des opérations suivantes : `coclass`, `progid`, ou `vi_progid`.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)  