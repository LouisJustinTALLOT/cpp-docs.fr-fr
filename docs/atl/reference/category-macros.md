---
title: Macros de catégorie
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 2b677ac6e7dac4eed5fc920ece064d94119ceb97
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168434"
---
# <a name="category-macros"></a>Macros de catégorie

Ces macros définissent des cartes de catégorie.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marque le début de la carte de catégorie.|
|[END_CATEGORY_MAP](#end_category_map)|Marque la fin de la carte de catégorie.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indique les catégories implémentées par l’objet COM.|
|[REQUIRED_CATEGORY](#required_category)|Indique les catégories qui sont requises par l’objet COM pour le conteneur.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="begin_category_map"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

Marque le début de la carte de catégorie.

```cpp
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
dans Nom de la classe contenant la carte de catégorie.

### <a name="remarks"></a>Notes

La carte de catégorie est utilisée pour spécifier les catégories de composants que la classe COM doit implémenter et les catégories requises à partir de son conteneur.

Ajoutez une entrée [IMPLEMENTED_CATEGORY](#implemented_category) à la carte pour chaque catégorie implémentée par la classe com. Ajoutez une entrée [REQUIRED_CATEGORY](#required_category) à la carte pour chaque catégorie dont les clients doivent implémenter la classe. Marquez la fin de la carte avec la macro [END_CATEGORY_MAP](#end_category_map) .

Les catégories de composants répertoriées dans le mappage sont inscrites automatiquement quand le module est inscrit si la classe a un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou un [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)associé.

> [!NOTE]
> ATL utilise le gestionnaire de catégories de composants standard pour inscrire les catégories de composants. Si le gestionnaire n’est pas présent sur le système lorsque le module est inscrit, l’inscription s’effectue correctement, mais les catégories de composants ne sont pas inscrites pour cette classe.

Pour plus d’informations sur les catégories de composants, consultez [que sont les catégories de composants et comment fonctionnent-ils](/windows/win32/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a>END_CATEGORY_MAP

Marque la fin de la carte de catégorie.

```cpp
END_CATEGORY_MAP()
```

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_CATEGORY_MAP](#begin_category_map).

## <a name="implemented_category"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Ajoutez une macro IMPLEMENTED_CATEGORY à la carte des [catégories](#begin_category_map) de votre composant pour spécifier qu’elle doit être enregistrée en tant qu’implémentation de la catégorie identifiée par le paramètre *CATID* .

```cpp
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Paramètres

*catID*<br/>
dans Constante ou variable CATID contenant l’identificateur global unique (GUID) de la catégorie implémentée. L’adresse du *CATID* sera prise et ajoutée au mappage. Reportez-vous au tableau ci-dessous pour sélectionner des catégories de stock.

### <a name="remarks"></a>Notes

Les catégories de composants répertoriées dans le mappage sont inscrites automatiquement quand le module est inscrit si la classe est associée à une [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou à une macro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .

Les clients peuvent utiliser les informations de catégorie inscrites pour la classe afin de déterminer ses fonctionnalités et exigences sans avoir à créer une instance de celle-ci.

Pour plus d’informations sur les catégories de composants, consultez [que sont les catégories de composants et comment fonctionnent-ils](/windows/win32/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="a-selection-of-stock-categories"></a>Sélection des catégories de stock

|Description|Symbole|GUID du Registre|
|-----------------|------------|-------------------|
|Sécurisé pour les scripts|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Sécurisé pour l’initialisation|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Relation contenant-contenu de site à cadre simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|liaison de données simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Liaison de données avancée|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Contrôles sans fenêtre|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objets prenant en charge Internet|Pour obtenir un exemple de liste, consultez [objets prenant en charge Internet](/windows/win32/com/internet-aware-objects) dans le SDK Windows.||

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a>REQUIRED_CATEGORY

Ajoutez une macro REQUIRED_CATEGORY à la carte des [catégories](#begin_category_map) de votre composant pour spécifier qu’elle doit être inscrite comme nécessitant la catégorie identifiée par le paramètre *CATID* .

```cpp
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Paramètres

*catID*<br/>
dans Constante ou variable CATID contenant l’identificateur global unique (GUID) de la catégorie requise. L’adresse du *CATID* sera prise et ajoutée au mappage. Reportez-vous au tableau ci-dessous pour sélectionner des catégories de stock.

### <a name="remarks"></a>Notes

Les catégories de composants répertoriées dans le mappage sont inscrites automatiquement quand le module est inscrit si la classe est associée à une [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou à une macro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .

Les clients peuvent utiliser les informations de catégorie inscrites pour la classe afin de déterminer ses fonctionnalités et exigences sans avoir à créer une instance de celle-ci. Par exemple, un contrôle peut exiger qu’un conteneur prenne en charge la liaison de données. Le conteneur peut déterminer s’il dispose des fonctionnalités nécessaires pour héberger le contrôle en interrogeant le gestionnaire de catégories pour connaître les catégories requises par ce contrôle. Si le conteneur ne prend pas en charge une fonctionnalité requise, il peut refuser l’hébergement de l’objet COM.

Pour plus d’informations sur les catégories de composants, y compris un exemple de liste, consultez [que sont les catégories de composants et comment fonctionnent-ils](/windows/win32/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="a-selection-of-stock-categories"></a>Sélection des catégories de stock

|Description|Symbole|GUID du Registre|
|-----------------|------------|-------------------|
|Sécurisé pour les scripts|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Sécurisé pour l’initialisation|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Relation contenant-contenu de site à cadre simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|liaison de données simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Liaison de données avancée|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Contrôles sans fenêtre|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objets prenant en charge Internet|Pour obtenir un exemple de liste, consultez [objets prenant en charge Internet](/windows/win32/com/internet-aware-objects) dans le SDK Windows.||

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
