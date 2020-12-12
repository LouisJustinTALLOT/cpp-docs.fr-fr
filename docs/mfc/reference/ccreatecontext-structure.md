---
description: 'En savoir plus sur : structure CCreateContext'
title: CCreateContext, structure
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: b0d8c3a38d4d6ce9ee6130092ea6b27a50ed15e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220459"
---
# <a name="ccreatecontext-structure"></a>CCreateContext, structure

L’infrastructure utilise la `CCreateContext` structure lorsqu’elle crée les fenêtres Frame et les vues associées à un document.

## <a name="syntax"></a>Syntaxe

```
struct CCreateContext
```

## <a name="remarks"></a>Notes

`CCreateContext` est une structure et n’a pas de classe de base.

Lorsque vous créez une fenêtre, les valeurs de cette structure fournissent les informations utilisées pour connecter les composants d’un document à la vue de ses données. Vous ne devez utiliser que `CCreateContext` si vous substituez des parties du processus de création.

Une `CCreateContext` structure contient des pointeurs vers le document, la fenêtre frame, la vue et le modèle de document. Il contient également un pointeur vers un `CRuntimeClass` qui identifie le type de vue à créer. Les informations de classe au moment de l’exécution et le pointeur de document actif sont utilisés pour créer une vue de manière dynamique. Le tableau suivant suggère comment et quand chaque `CCreateContext` membre peut être utilisé :

|Membre|Type|Présentation|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` de la nouvelle vue à créer.|
|`m_pCurrentDoc`|`CDocument*`|Document existant à associer à la nouvelle vue.|
|`m_pNewDocTemplate`|`CDocTemplate*`|Modèle de document associé à la création d’une nouvelle fenêtre frame MDI.|
|`m_pLastView`|`CView*`|Vue d’origine sur laquelle des vues supplémentaires sont modélisées, comme dans la création de vues de fenêtres fractionnées ou la création d’une deuxième vue sur un document.|
|`m_pCurrentFrame`|`CFrameWnd*`|Fenêtre frame sur laquelle les fenêtres Frame supplémentaires sont modélisées, comme dans la création d’une deuxième fenêtre frame sur un document.|

Lorsqu’un modèle de document crée un document et ses composants associés, il valide les informations stockées dans la `CCreateContext` structure. Par exemple, une vue ne doit pas être créée pour un document inexistant.

> [!NOTE]
> Tous les pointeurs dans `CCreateContext` sont facultatifs et peuvent être `NULL` si non spécifiés ou inconnus.

`CCreateContext` est utilisé par les fonctions membres listées sous « Voir aussi ». Pour obtenir des informations spécifiques, consultez les descriptions de ces fonctions si vous envisagez de les remplacer.

Voici quelques recommandations générales :

- Lorsqu’il est passé comme argument pour la création de la fenêtre, comme dans `CWnd::Create` , `CFrameWnd::Create` et `CFrameWnd::LoadFrame` , le contexte de création spécifie à quoi la nouvelle fenêtre doit être connectée. Pour la plupart des fenêtres, la structure entière est facultative et un `NULL` pointeur peut être passé.

- Pour les fonctions membres substituables, telles que `CFrameWnd::OnCreateClient` , l' `CCreateContext` argument est facultatif.

- Pour les fonctions membres impliquées dans la création d’une vue, vous devez fournir suffisamment d’informations pour créer la vue. Par exemple, pour la première vue d’une fenêtre fractionnée, vous devez fournir les informations de la classe d’affichage et le document actif.

En général, si vous utilisez les paramètres par défaut de l’infrastructure, vous pouvez ignorer `CCreateContext` . Si vous tentez d’effectuer des modifications plus avancées, le bibliothèque MFC (Microsoft Foundation Class) code source ou les exemples de programmes, tels que VIEWEX, vous guideront. Si vous oubliez un paramètre obligatoire, une assertion de Framework vous indique ce que vous avez oublié.

Pour plus d’informations sur `CCreateContext` , consultez l’exemple MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd :: Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd :: LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd :: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd :: Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd :: CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
