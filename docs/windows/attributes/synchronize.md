---
description: 'En savoir plus sur : synchroniser'
title: Synchronize (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: bbee19406396e4041b4d7ca1e2acf2b8d7193494
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329550"
---
# <a name="synchronize"></a>synchronize

Synchronise l’accès à la méthode cible.

## <a name="syntax"></a>Syntaxe

```cpp
[synchronize]
```

## <a name="remarks"></a>Notes

L’attribut C++ **Synchronize** implémente la prise en charge de la synchronisation de la méthode cible d’un objet. La synchronisation permet à plusieurs objets d’utiliser une ressource commune (telle qu’une méthode d’une classe) en contrôlant l’accès de la méthode cible.

Le code inséré par cet attribut appelle la `Lock` méthode appropriée (déterminée par le modèle de thread) au début de la méthode cible. Lorsque la méthode est fermée, `Unlock` est appelé automatiquement. Pour plus d’informations sur ces fonctions, consultez [CComAutoThreadModule :: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

Cet attribut exige que l’attribut [coclass](coclass.md), [progid](progid.md)ou [vi_progid](vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément. Si un attribut unique est utilisé, les deux autres sont appliqués automatiquement. Par exemple, si `progid` est appliqué, `vi_progid` et `coclass` sont également appliqués.

## <a name="example"></a>Exemple

Le code suivant fournit la synchronisation pour la `UpdateBalance` méthode de l' `CMyClass` objet.

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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode de classe, méthode|
|**Renouvelable**|Non|
|**Attributs requis**|Une ou plusieurs des valeurs suivantes : `coclass` , `progid` ou `vi_progid` .|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs COM](com-attributes.md)
