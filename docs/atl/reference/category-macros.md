---
title: Macros de catégorie
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 1d8bbae4608aa661bbc612604f7d85855f325f5f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321598"
---
# <a name="category-macros"></a>Macros de catégorie

Ces macros définissent les cartes de catégorie.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marque le début de la carte de catégorie.|
|[END_CATEGORY_MAP](#end_category_map)|Marque la fin de la carte de catégorie.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indique les catégories qui sont mises en œuvre par l’objet COM.|
|[REQUIRED_CATEGORY](#required_category)|Indique les catégories requises du conteneur par l’objet COM.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="begin_category_map"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

Marque le début de la carte de catégorie.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
[dans] Le nom de la classe contenant la carte de la catégorie.

### <a name="remarks"></a>Notes

La carte de catégorie est utilisée pour spécifier les catégories de composants que la classe COM mettra en œuvre et les catégories dont elle a besoin à partir de son conteneur.

Ajoutez une [entrée IMPLEMENTED_CATEGORY](#implemented_category) à la carte pour chaque catégorie mise en œuvre par la classe COM. Ajoutez une [entrée REQUIRED_CATEGORY](#required_category) à la carte pour chaque catégorie que la classe exige que ses clients mettent en œuvre. Marquez la fin de la carte avec la [macro END_CATEGORY_MAP.](#end_category_map)

Les catégories de composants énumérées sur la carte seront enregistrées automatiquement lorsque le module est enregistré si la classe a un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)associés .

> [!NOTE]
> ATL utilise le gestionnaire des catégories de composants standard pour enregistrer les catégories de composants. Si le gestionnaire n’est pas présent sur le système lorsque le module est enregistré, l’inscription réussit, mais les catégories de composants ne seront pas enregistrées pour cette catégorie.

Pour plus d’informations sur les catégories de composants, voir [Quelles sont les catégories de composants et comment fonctionnent-elles](/windows/win32/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a>END_CATEGORY_MAP

Marque la fin de la carte de catégorie.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_CATEGORY_MAP](#begin_category_map).

## <a name="implemented_category"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Ajoutez une macro IMPLEMENTED_CATEGORY à la [carte](#begin_category_map) de catégorie de votre composant pour spécifier qu’il doit être enregistré comme implémentation de la catégorie identifiée par le paramètre *catID.*

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Paramètres

*catID catID*<br/>
[dans] Une constante OU une variable CATID tenant l’identifiant unique à l’échelle mondiale (GUID) pour la catégorie mise en œuvre. L’adresse du *catID* sera prise et ajoutée à la carte. Voir le tableau ci-dessous pour une sélection de catégories d’actions.

### <a name="remarks"></a>Notes

Les catégories de composants répertoriées dans la carte seront enregistrées automatiquement lorsque le module est enregistré si la classe a un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) associé ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.

Les clients peuvent utiliser les informations de catégorie enregistrées pour la classe pour déterminer ses capacités et ses exigences sans avoir à en créer une instance.

Pour plus d’informations sur les catégories de composants, voir [Quelles sont les catégories de composants et comment fonctionnent-elles](/windows/win32/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="a-selection-of-stock-categories"></a>Une sélection de catégories d’actions

|Description|Symbole|Registre GUID|
|-----------------|------------|-------------------|
|Coffre-fort pour script|CATID_SafeForScripting|7DD95801-9882-11CF-9FA9-00AA006C42C4|
|Coffre-fort pour l’initialisation|CATID_SafeForInitializing|7DD95802-9882-11CF-9FA9-00AA006C42C4|
|Contenu simple du site de cadre|CATID_SimpleFrameControl|157083E0-2368-11cf-87B9-00AA006C8166|
|liaison de données simple|CATID_PropertyNotifyControl|157083E1-2368-11cf-87B9-00AA006C8166|
|Liaison de données avancée|CATID_VBDataBound|157083E2-2368-11cf-87B9-00AA006C8166|
|Contrôles sans fenêtre|CATID_WindowlessObject|1D06B600-3AE3-11cf-87B9-00AA006C8166|
|Objets conscients d’Internet|Consultez [Les objets conscients d’Internet](/windows/win32/com/internet-aware-objects) dans le SDK Windows pour une liste d’échantillons.||

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a>REQUIRED_CATEGORY

Ajoutez une macro REQUIRED_CATEGORY à la [carte](#begin_category_map) de catégorie de votre composant pour spécifier qu’elle doit être enregistrée comme exigeant la catégorie identifiée par le paramètre *catID.*

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Paramètres

*catID catID*<br/>
[dans] Une constante OU une variable CATID tenant l’identifiant unique à l’échelle mondiale (GUID) pour la catégorie requise. L’adresse du *catID* sera prise et ajoutée à la carte. Voir le tableau ci-dessous pour une sélection de catégories d’actions.

### <a name="remarks"></a>Notes

Les catégories de composants répertoriées dans la carte seront enregistrées automatiquement lorsque le module est enregistré si la classe a un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) associé ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.

Les clients peuvent utiliser les informations de catégorie enregistrées pour la classe pour déterminer ses capacités et ses exigences sans avoir à en créer une instance. Par exemple, un contrôle peut exiger qu’un support de conteneurs soit contraignant. Le conteneur peut savoir s’il a les capacités nécessaires pour accueillir le contrôle en interrogeant le gestionnaire de catégorie pour les catégories requises par ce contrôle. Si le conteneur ne prend pas en charge une fonctionnalité requise, il peut refuser d’héberger l’objet COM.

Pour plus d’informations sur les catégories de composants, y compris une liste d’échantillons, voir [Quelles sont les catégories de composants et comment fonctionnent-elles](/windows/win32/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="a-selection-of-stock-categories"></a>Une sélection de catégories d’actions

|Description|Symbole|Registre GUID|
|-----------------|------------|-------------------|
|Coffre-fort pour script|CATID_SafeForScripting|7DD95801-9882-11CF-9FA9-00AA006C42C4|
|Coffre-fort pour l’initialisation|CATID_SafeForInitializing|7DD95802-9882-11CF-9FA9-00AA006C42C4|
|Contenu simple du site de cadre|CATID_SimpleFrameControl|157083E0-2368-11cf-87B9-00AA006C8166|
|liaison de données simple|CATID_PropertyNotifyControl|157083E1-2368-11cf-87B9-00AA006C8166|
|Liaison de données avancée|CATID_VBDataBound|157083E2-2368-11cf-87B9-00AA006C8166|
|Contrôles sans fenêtre|CATID_WindowlessObject|1D06B600-3AE3-11cf-87B9-00AA006C8166|
|Objets conscients d’Internet|Consultez [Les objets conscients d’Internet](/windows/win32/com/internet-aware-objects) dans le SDK Windows pour une liste d’échantillons.||

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
