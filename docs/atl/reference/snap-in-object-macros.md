---
title: Macros d’objet Snap-In
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
ms.openlocfilehash: 6a57cdb3c9b6a4448bc954ff754ac9b18fa0b393
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325858"
---
# <a name="snap-in-object-macros"></a>Macros d’objet Snap-In

Ces macros fournissent un support pour les extensions de snap-in.

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Marque le début de la carte de classe de données d’extension snap-in pour un objet Snap-In.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Marque le début de la carte de la barre d’outils pour un objet Snap-In.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Marque la fin de la carte de classe de données d’extension snap-in pour un objet Snap-In.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Marque la fin de la carte de la barre d’outils pour un objet Snap-In.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Crée un membre de données pour la classe de données de l’extension snap-in.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Entre une classe de données d’extension instantanée dans la carte de classe de données d’extension snap-in de l’objet Snap-In.|
|[SNAPINMENUID](#snapinmenuid)|Déclare l’ID du menu contextuelle utilisé par l’objet Snap-In.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Entre une barre d’outils dans la carte de la barre d’outils de l’objet Snap-In.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlsnap.h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Marque le début de la carte de classe de données d’extension snap-in.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Paramètres

*Classname*<br/>
[dans] Le nom de la classe de données d’extension snap-in.

### <a name="remarks"></a>Notes

Démarrez votre carte d’extension snap-in avec la macro BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP, ajoutez des entrées pour chacun de vos types de données d’extension snap-in avec la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY,](#extension_snapin_nodeinfo_entry) et complétez la carte avec la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP

Déclare le début de la carte d’identification de la barre d’outils pour l’objet Snap-In.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Paramètres

*_class*<br/>
[dans] Spécifie la classe d’objets Snap-In.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP

Marque la fin de la carte de classe de données d’extension snap-in.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Notes

Démarrez votre carte d’extension snap-in avec la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP,](#begin_extension_snapin_nodeinfo_map) ajoutez des entrées pour chacun de vos types de données d’extension snap-in avec la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY,](#extension_snapin_nodeinfo_entry) et complétez la carte avec la macro END_EXTENSION_SNAPIN_NODEINFO_MAP.

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP

Déclare la fin de la carte d’identification de la barre d’outils pour l’objet Snap-In.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Paramètres

*_class*<br/>
[dans] Spécifie la classe d’objets Snap-In.

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS

Ajoute un membre de données à la classe de données d’extension snap-in pour une classe **dérivée d’ISnapInItemImpl.**

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Paramètres

*donnéesClass*<br/>
[dans] La classe de données de l’extension snap-in.

### <a name="remarks"></a>Notes

Cette classe doit également être saisie dans une carte de classe de données d’extension instantanée. Démarrez votre carte de classe de données d’extension snap-in avec la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP,](#begin_extension_snapin_nodeinfo_map) ajoutez des entrées pour chacun de vos types de données d’extension snap-in avec la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY,](#extension_snapin_nodeinfo_entry) et complétez la carte avec la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY

Ajoute une classe de données d’extension snap-in à la carte de classe de données d’extension snap-in.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Paramètres

*donnéesClass*<br/>
[dans] La classe de données de l’extension snap-in.

### <a name="remarks"></a>Notes

Démarrez votre carte de classe de données d’extension snap-in avec la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP,](#begin_extension_snapin_nodeinfo_map) ajoutez des entrées pour chacun de vos types de données d’extension snap-in avec la macro EXTENSION_SNAPIN_NODEINFO_ENTRY, et complétez la carte avec la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a>SNAPINMENUID

Utilisez cette macro pour déclarer la ressource de menu contextuelle de l’objet Snap-In.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] Identifie le menu contextuelle de l’objet Snap-In.

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY

Utilisez cette macro pour entrer une pièce d’identité de barre d’outils dans la carte d’identification de la barre d’outils de l’objet Snap-In.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] Identifie le contrôle de la barre d’outils.

### <a name="remarks"></a>Notes

La macro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) marque le début de la carte d’identification de la barre d’outils; [l’END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) macro marque la fin.

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
