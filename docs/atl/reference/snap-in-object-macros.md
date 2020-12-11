---
description: En savoir plus sur les macros d’objets Snap-In
title: Macros d’objets Snap-In
ms.date: 11/04/2016
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
ms.openlocfilehash: d775c1d5f66f16fb63b9a7adeda2bc8e74046acf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157683"
---
# <a name="snap-in-object-macros"></a>Macros d’objets Snap-In

Ces macros assurent la prise en charge des extensions de composant logiciel enfichable.

|Nom|Description|
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Marque le début de la classe de mappage des données d’extension du composant logiciel enfichable pour un objet Snap-In.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Marque le début de la carte de barre d’outils pour un objet Snap-In.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Marque la fin du mappage de classe de données d’extension de composant logiciel enfichable pour un objet Snap-In.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Marque la fin de la carte de barre d’outils pour un objet Snap-In.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Crée un membre de données pour la classe de données de l’extension de composant logiciel enfichable.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Entre une classe de données d’extension de composant logiciel enfichable dans le mappage de classes de données d’extension de composant logiciel enfichable de l’objet Snap-In.|
|[SNAPINMENUID](#snapinmenuid)|Déclare l’ID du menu contextuel utilisé par l’objet Snap-In.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Entre une barre d’outils dans le mappage de barre d’outils de l’objet Snap-In.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlsnap. h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a> BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Marque le début de la carte des classes de données d’extension du composant logiciel enfichable.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Paramètres

*NomClasse*<br/>
dans Nom de la classe de données d’extension du composant logiciel enfichable.

### <a name="remarks"></a>Notes

Démarrez votre mappage d’extension de composant logiciel enfichable avec la macro BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP, ajoutez des entrées pour chacun de vos types de données d’extension de composant logiciel enfichable avec la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) et complétez la carte avec la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a> BEGIN_SNAPINTOOLBARID_MAP

Déclare le début de la carte de l’ID de barre d’outils pour l’objet Snap-In.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Paramètres

*_class*<br/>
dans Spécifie la classe d’objets Snap-In.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a> END_EXTENSION_SNAPIN_NODEINFO_MAP

Marque la fin du mappage de classe de données d’extension du composant logiciel enfichable.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Notes

Démarrez votre mappage d’extension de composant logiciel enfichable avec la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) , ajoutez des entrées pour chacun de vos types de données de composant logiciel enfichable d’extension avec la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) et complétez la carte avec la macro END_EXTENSION_SNAPIN_NODEINFO_MAP.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a> END_SNAPINTOOLBARID_MAP

Déclare la fin de la carte de l’ID de barre d’outils pour l’objet Snap-In.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Paramètres

*_class*<br/>
dans Spécifie la classe d’objets Snap-In.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a> EXTENSION_SNAPIN_DATACLASS

Ajoute un membre de données à la classe de données d’extension de composant logiciel enfichable pour une classe dérivée de **ISnapInItemImpl**.

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Paramètres

*dataClass*<br/>
dans Classe de données de l’extension de composant logiciel enfichable.

### <a name="remarks"></a>Notes

Cette classe doit également être entrée dans un mappage de classes de données d’extension de composant logiciel enfichable. Démarrez votre mappage de classe de données d’extension de composant logiciel enfichable avec la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) , ajoutez des entrées pour chacun de vos types de données d’extension de composant logiciel enfichable avec la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) et complétez la carte avec la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a> EXTENSION_SNAPIN_NODEINFO_ENTRY

Ajoute une classe de données d’extension de composant logiciel enfichable au mappage de classe de données d’extension de composant logiciel enfichable.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Paramètres

*dataClass*<br/>
dans Classe de données de l’extension de composant logiciel enfichable.

### <a name="remarks"></a>Notes

Démarrez votre mappage de classe de données d’extension de composant logiciel enfichable avec la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) , ajoutez des entrées pour chacun de vos types de données d’extension de composant logiciel enfichable avec la macro EXTENSION_SNAPIN_NODEINFO_ENTRY et complétez la carte avec la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) .

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a> SNAPINMENUID

Utilisez cette macro pour déclarer la ressource de menu contextuel de l’objet Snap-In.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identifie le menu contextuel de l’objet Snap-In.

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a> SNAPINTOOLBARID_ENTRY

Utilisez cette macro pour entrer un ID de barre d’outils dans le mappage de l’ID de barre d’outils de l’objet Snap-In.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identifie le contrôle ToolBar.

### <a name="remarks"></a>Notes

La macro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) marque le début de la carte de l’ID de barre d’outils ; la macro [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) marque la fin.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
