---
title: Ccreatecontext, Structure
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 795b20cba41eeca8cc1a32e312edf065b718f364
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768484"
---
# <a name="ccreatecontext-structure"></a>Ccreatecontext, Structure

L’infrastructure utilise le `CCreateContext` structure lorsqu’il crée les fenêtres frame et les vues qui sont associés à un document.

## <a name="syntax"></a>Syntaxe

```
struct CCreateContext
```

## <a name="remarks"></a>Notes

`CCreateContext` est une structure et ne dispose pas d’une classe de base.

Lorsque vous créez une fenêtre, les valeurs dans cette structure fournissent les informations utilisées pour connecter les composants d’un document à la vue de ses données. Vous devez uniquement utiliser `CCreateContext` si vous substituez des parties du processus de création.

Un `CCreateContext` structure contient des pointeurs vers le document, la fenêtre frame, la vue et le modèle de document. Il contient également un pointeur vers un `CRuntimeClass` qui identifie le type de vue à créer. Les informations de classe d’exécution et le pointeur de document en cours sont utilisés pour créer une nouvelle vue dynamiquement. Le tableau suivant suggère comment et quand chaque `CCreateContext` membre peut être utilisé :

|Membre|Type|Il concerne|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` de la nouvelle vue à créer.|
|`m_pCurrentDoc`|`CDocument*`|Le document existant à associer à la nouvelle vue.|
|`m_pNewDocTemplate`|`CDocTemplate*`|Le modèle de document associé à la création d’une fenêtre frame MDI.|
|`m_pLastView`|`CView*`|La vue d’origine sur lequel des vues supplémentaires sont modélisées, comme dans la création de vues de fenêtre de séparateur ou la création d’une deuxième vue sur un document.|
|`m_pCurrentFrame`|`CFrameWnd*`|La fenêtre frame sur lequel sont modélisés fenêtres frame supplémentaires, comme dans la création d’une deuxième fenêtre frame sur un document.|

Lorsqu’un modèle de document crée un document et ses composants associés, il valide les informations stockées dans le `CCreateContext` structure. Par exemple, une vue ne doit pas être créée pour un document qui n’existe pas.

> [!NOTE]
>  Tous les pointeurs dans `CCreateContext` sont facultatives et peuvent être `NULL` si non spécifié ou inconnu.

`CCreateContext` est utilisé par les fonctions membres répertoriées sous « Voir aussi ». Pour plus d’informations, consultez les descriptions de ces fonctions si vous envisagez de les remplacer.

Voici quelques recommandations générales :

- Quand il est passé en tant qu’argument pour la création de la fenêtre, comme dans `CWnd::Create`, `CFrameWnd::Create`, et `CFrameWnd::LoadFrame`, le contexte de créer spécifie ce à quoi la nouvelle fenêtre doit être connectée. Pour la plupart des fenêtres, la structure entière est facultative et un `NULL` pointeur peut être passé.

- Pour les fonctions membres substituables, tels que `CFrameWnd::OnCreateClient`, le `CCreateContext` argument est facultatif.

- Pour les fonctions membres impliquées dans la vue Création, vous devez fournir suffisamment d’informations pour créer la vue. Par exemple, pour la première vue dans une fenêtre fractionnée, vous devez fournir les informations de classe de vue et le document actif.

En règle générale, si vous utilisez les valeurs par défaut de framework, vous pouvez ignorer `CCreateContext`. Si vous essayez de modifications plus complexes, le code source de Microsoft Foundation Class Library ou les exemples de programmes, tels que VIEWEX, vous guide. Si vous n’oubliez pas un paramètre obligatoire, une assertion de framework vous indique ce que vous avez oublié.

Pour plus d’informations sur `CCreateContext`, consultez l’exemple MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** afxext.h

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
