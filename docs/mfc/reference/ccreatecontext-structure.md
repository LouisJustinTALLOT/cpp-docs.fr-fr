---
title: CCreateContext Structure
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 29fc6210b9888b6a5ba5aaf15b66242c29c15dc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369380"
---
# <a name="ccreatecontext-structure"></a>CCreateContext Structure

Le cadre `CCreateContext` utilise la structure lorsqu’il crée les fenêtres et les vues de cadre qui sont associées à un document.

## <a name="syntax"></a>Syntaxe

```
struct CCreateContext
```

## <a name="remarks"></a>Notes

`CCreateContext`est une structure et n’a pas de classe de base.

Lorsque vous créez une fenêtre, les valeurs de cette structure fournissent les informations utilisées pour connecter les composants d’un document à la vue de ses données. Vous n’avez `CCreateContext` qu’à utiliser si vous êtes en train de prépondérer des parties du processus de création.

Une `CCreateContext` structure contient des indications sur le document, la fenêtre du cadre, la vue et le modèle de document. Il contient également un `CRuntimeClass` pointeur à un qui identifie le type de vue à créer. Les informations de classe de temps d’exécution et le pointeur de document actuel sont utilisés pour créer une nouvelle vue dynamiquement. Le tableau suivant suggère `CCreateContext` comment et quand chaque membre pourrait être utilisé :

|Membre|Type|À quoi ça s’en va|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`de la nouvelle vue à créer.|
|`m_pCurrentDoc`|`CDocument*`|Le document existant à associer à la nouvelle vue.|
|`m_pNewDocTemplate`|`CDocTemplate*`|Le modèle de document associé à la création d’une nouvelle fenêtre de cadre MDI.|
|`m_pLastView`|`CView*`|La vue originale sur laquelle des vues supplémentaires sont modélisées, comme dans la création de vues de fenêtre de splitter ou la création d’une deuxième vue sur un document.|
|`m_pCurrentFrame`|`CFrameWnd*`|La fenêtre de cadre sur laquelle les fenêtres de cadre supplémentaires sont modélisées, comme dans la création d’une deuxième fenêtre de cadre sur un document.|

Lorsqu’un modèle de document crée un document et ses composants `CCreateContext` associés, il valide les informations stockées dans la structure. Par exemple, une vue ne devrait pas être créée pour un document inexistant.

> [!NOTE]
> Tous les pointeurs `CCreateContext` sont facultatifs et peuvent être `NULL` spécifiés ou inconnus.

`CCreateContext`est utilisé par les fonctions membres énumérées dans "Voir aussi." Consultez les descriptions de ces fonctions pour obtenir des informations spécifiques si vous prévoyez de les remplacer.

Voici quelques lignes directrices générales :

- Lorsqu’il est adopté comme un `CWnd::Create` `CFrameWnd::Create`argument `CFrameWnd::LoadFrame`pour la création de fenêtre, comme dans , , et , le contexte de création précise ce que la nouvelle fenêtre doit être connecté à. Pour la plupart des fenêtres, `NULL` toute la structure est facultative et un pointeur peut être passé.

- Pour les fonctions de membre `CFrameWnd::OnCreateClient`primordiales, telles que, l’argument `CCreateContext` est facultatif.

- Pour les fonctions de membre impliquées dans la création de vue, vous devez fournir suffisamment d’informations pour créer la vue. Par exemple, pour la première vue dans une fenêtre de splitter, vous devez fournir les informations de classe de vue et le document actuel.

En général, si vous utilisez les défauts de cadre, vous pouvez ignorer `CCreateContext`. Si vous tentez des modifications plus avancées, le code source Microsoft Foundation Class Library ou les programmes d’exemple, tels que VIEWEX, vous guideront. Si vous oubliez un paramètre requis, une affirmation de cadre vous dira ce que vous avez oublié.

Pour plus `CCreateContext`d’informations sur , voir l’échantillon MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Créer](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Créer](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
