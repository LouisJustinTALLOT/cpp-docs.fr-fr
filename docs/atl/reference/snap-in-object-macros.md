---
title: Macros d’objet du composant logiciel enfichable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
dev_langs:
- C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d37c8c9d319495c3247bf98d9ed3c8f58063ae56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050552"
---
# <a name="snap-in-object-macros"></a>Macros d’objet du composant logiciel enfichable

Ces macros fournissent la prise en charge pour les extensions de composant logiciel enfichable.

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Marque le début de l’extension du composant logiciel enfichable classe du mappage de données pour un objet Snap-In.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Marque le début de la carte de la barre d’outils pour un objet Snap-In.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Marque la fin de l’extension du composant logiciel enfichable classe du mappage de données pour un objet Snap-In.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Marque la fin de la carte de la barre d’outils pour un objet Snap-In.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Crée un membre de données pour la classe de données de l’extension du composant logiciel enfichable.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Passe à une classe de données d’extension du composant logiciel enfichable dans le mappage de classe de données extension composant logiciel enfichable de l’objet Snap-In.|
|[SNAPINMENUID](#snapinmenuid)|Déclare l’ID du menu contextuel utilisé par l’objet Snap-In.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Insère une barre d’outils dans le mappage de la barre d’outils de l’objet Snap-In.|  

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsnap.h

##  <a name="begin_extension_snapin_nodeinfo_map"></a>  BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Marque le début de la carte de classe de données extension composant logiciel enfichable.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Paramètres

*classname*<br/>
[in] Le nom de la classe de données d’extension du composant logiciel enfichable.

### <a name="remarks"></a>Notes

Démarrer votre carte d’extension du composant logiciel enfichable avec la macro BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP, ajoutez des entrées pour chacun de vos types de données de composant logiciel enfichable extension avec le [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) (macro) et effectuer un mappage avec le [ END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) (macro).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="begin_snapintoolbarid_map"></a>  BEGIN_SNAPINTOOLBARID_MAP

Déclare le début de la carte d’ID de barre d’outils pour l’objet Snap-In.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Paramètres

*_classe*<br/>
[in] Spécifie la classe d’objet Snap-In.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

##  <a name="end_extension_snapin_nodeinfo_map"></a>  END_EXTENSION_SNAPIN_NODEINFO_MAP

Marque la fin de l’extension du composant logiciel enfichable classe du mappage de données.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Notes

Démarrez votre carte d’extension du composant logiciel enfichable avec le [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) macro, ajouter des entrées pour chacun de vos types de données du composant logiciel enfichable d’extension avec la [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) (macro), et effectuez le mappage avec la macro END_EXTENSION_SNAPIN_NODEINFO_MAP.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

##  <a name="end_snapintoolbarid_map"></a>  END_SNAPINTOOLBARID_MAP

Déclare la fin de la carte d’ID de barre d’outils pour l’objet Snap-In.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Paramètres

*_classe*<br/>
[in] Spécifie la classe d’objet Snap-In.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

##  <a name="extension_snapin_dataclass"></a>  EXTENSION_SNAPIN_DATACLASS

Ajoute un membre de données à la classe de données d’extension du composant logiciel enfichable pour un **ISnapInItemImpl**-classe dérivée.

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Paramètres

*dataClass*<br/>
[in] La classe de données de l’extension du composant logiciel enfichable.

### <a name="remarks"></a>Notes

Cette classe doit également être entrée dans un mappage de classe de données de composant logiciel enfichable dans l’extension. Démarrez votre mappage de classe de données de composant logiciel enfichable extension avec le [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) (macro), ajouter des entrées pour chacun de vos types de données de composant logiciel enfichable extension avec le [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)(macro) et effectuer un mappage avec le [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) (macro).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="extension_snapin_nodeinfo_entry"></a>  EXTENSION_SNAPIN_NODEINFO_ENTRY

Ajoute une classe de données d’extension du composant logiciel enfichable pour le mappage de classe de données de composant logiciel enfichable dans l’extension.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Paramètres

*dataClass*<br/>
[in] La classe de données de l’extension du composant logiciel enfichable.

### <a name="remarks"></a>Notes

Démarrez votre mappage de classe de données de composant logiciel enfichable extension avec le [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) (macro), ajouter des entrées pour chacun de vos types de données de composant logiciel enfichable extension avec la macro EXTENSION_SNAPIN_NODEINFO_ENTRY et effectuer un mappage avec le [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) (macro).

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

##  <a name="snapinmenuid"></a>  SNAPINMENUID

Utilisez cette macro pour déclarer la ressource de menu contextuel de l’objet Snap-In.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] Identifie le menu contextuel de l’objet Snap-In.

##  <a name="snapintoolbarid_entry"></a>  SNAPINTOOLBARID_ENTRY

Utilisez cette macro à entrer un ID de barre d’outils dans le mappage de ID de barre d’outils de composant logiciel enfichable dans l’objet.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] Identifie le contrôle de barre d’outils.

### <a name="remarks"></a>Notes

Le [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) macro marque le début de la carte d’ID de barre d’outils ; le [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) macro marque la fin.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
