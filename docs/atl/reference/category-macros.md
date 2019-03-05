---
title: Macros de catégorie
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 1ee6ab07ee72155acae552da933167b56af72a17
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263843"
---
# <a name="category-macros"></a>Macros de catégorie

Ces macros définissent les mappages de catégorie.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marque le début de la carte de catégorie.|
|[END_CATEGORY_MAP](#end_category_map)|Marque la fin de la carte de catégorie.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indique les catégories qui sont implémentées par l’objet COM.|
|[REQUIRED_CATEGORY](#required_category)|Indique les catégories qui sont requises du conteneur par l’objet COM.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP

Marque le début de la carte de catégorie.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
[in] Le nom de la classe contenant le mappage de catégorie.

### <a name="remarks"></a>Notes

Le mappage de catégorie est utilisé pour spécifier les catégories de composant implémente la classe COM et les catégories dans lesquelles il requiert de son conteneur.

Ajouter un [IMPLEMENTED_CATEGORY](#implemented_category) entrée dans le mappage pour chaque catégorie implémenté par la classe COM. Ajouter un [REQUIRED_CATEGORY](#required_category) entrée à la carte pour chaque catégorie de la classe nécessitant ses clients à implémenter. Marquer la fin de la carte avec le [END_CATEGORY_MAP](#end_category_map) (macro).

Les catégories de composants répertoriés dans le mappage seront inscrit automatiquement lorsque le module est enregistré si la classe est associé à un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .

> [!NOTE]
>  ATL utilise le Gestionnaire de catégories de composants standard pour enregistrer les catégories de composants. Si le gestionnaire n’est pas présent sur le système lorsque le module est enregistré, l’inscription réussit, mais les catégories de composant ne seront pas enregistrés pour cette classe.

Pour plus d’informations sur les catégories de composants, consultez [quelles sont les catégories de composants et comment elles fonctionnent](/windows/desktop/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>  END_CATEGORY_MAP

Marque la fin de la carte de catégorie.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_CATEGORY_MAP](#begin_category_map).

##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY

Ajouter une macro IMPLEMENTED_CATEGORY à de votre composant [correspondance des catégories](#begin_category_map) pour spécifier qu’il doit être inscrit en tant que l’implémentation de la catégorie identifiée par le *catID* paramètre.

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Paramètres

*catID*<br/>
[in] CATID constante ou variable qui contient l’identificateur global unique (GUID) pour la catégorie implémentée. L’adresse de *catID* seront effectuées et ajoutée à la carte. Consultez le tableau ci-dessous pour une sélection des catégories de stock.

### <a name="remarks"></a>Notes

Les catégories de composants répertoriés dans le mappage seront inscrit automatiquement lorsque le module est enregistré si la classe est associé à un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.

Les clients peuvent utiliser les informations de catégorie inscrits pour la classe pour déterminer ses fonctionnalités et les exigences sans avoir à créer une instance de celle-ci.

Pour plus d’informations sur les catégories de composants, consultez [quelles sont les catégories de composants et comment elles fonctionnent](/windows/desktop/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="a-selection-of-stock-categories"></a>Une sélection des catégories de Stock

|Description|Symbole|GUID de Registre|
|-----------------|------------|-------------------|
|Safe pour le script|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Sûr pour l’initialisation|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Relation contenant-contenu de cadre simple Site|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|liaison de données simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Liaison de données avancée|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Contrôles sans fenêtre|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objets prenant en charge Internet|Consultez [Internet des objets prenant en charge](/windows/desktop/com/internet-aware-objects) dans le SDK Windows pour un exemple de liste.||

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>  REQUIRED_CATEGORY

Ajouter une macro REQUIRED_CATEGORY à de votre composant [correspondance des catégories](#begin_category_map) pour spécifier qu’il doit être inscrit comme nécessitant la catégorie identifiée par le *catID* paramètre.

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Paramètres

*catID*<br/>
[in] CATID constante ou variable qui contient l’identificateur global unique (GUID) pour la catégorie obligatoire. L’adresse de *catID* seront effectuées et ajoutée à la carte. Consultez le tableau ci-dessous pour une sélection des catégories de stock.

### <a name="remarks"></a>Notes

Les catégories de composants répertoriés dans le mappage seront inscrit automatiquement lorsque le module est enregistré si la classe est associé à un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.

Les clients peuvent utiliser les informations de catégorie inscrits pour la classe pour déterminer ses fonctionnalités et les exigences sans avoir à créer une instance de celle-ci. Par exemple, un contrôle peut nécessiter qu’un conteneur prend en charge la liaison de données. Le conteneur peut savoir s’il a les fonctionnalités nécessaires pour héberger le contrôle en interrogeant le Gestionnaire de catégorie pour les catégories requises par ce contrôle. Si le conteneur ne prend pas en charge une fonctionnalité requise, elle peut refuser héberger l’objet COM.

Pour plus d’informations sur les catégories de composants, notamment une liste d’exemples, consultez [quelles sont les catégories de composants et comment elles fonctionnent](/windows/desktop/com/component-categories-and-how-they-work) dans le SDK Windows.

### <a name="a-selection-of-stock-categories"></a>Une sélection des catégories de Stock

|Description|Symbole|GUID de Registre|
|-----------------|------------|-------------------|
|Safe pour le script|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Sûr pour l’initialisation|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Relation contenant-contenu de cadre simple Site|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|liaison de données simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Liaison de données avancée|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Contrôles sans fenêtre|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objets prenant en charge Internet|Consultez [Internet des objets prenant en charge](/windows/desktop/com/internet-aware-objects) dans le SDK Windows pour un exemple de liste.||

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
