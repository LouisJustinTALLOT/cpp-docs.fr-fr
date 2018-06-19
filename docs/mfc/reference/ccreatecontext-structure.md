---
title: Structure de CCreateContext | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCreateContext
dev_langs:
- C++
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af6e81b9215aa6e7bc9e5f294a1d95aee4b51321
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352042"
---
# <a name="ccreatecontext-structure"></a>Structure de CCreateContext
L’infrastructure utilise le `CCreateContext` lorsqu’il crée les fenêtres frame et les vues qui sont associés à un document de la structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CCreateContext  
```  
  
## <a name="remarks"></a>Notes  
 `CCreateContext` est une structure et ne dispose pas d’une classe de base.  
  
 Lorsque vous créez une fenêtre, les valeurs dans cette structure fournissent les informations utilisées pour connecter les composants d’un document à l’affichage de ses données. Vous devez uniquement utiliser `CCreateContext` si vous substituez les parties du processus de création.  
  
 A `CCreateContext` structure contient des pointeurs vers le document, la fenêtre frame, la vue et le modèle de document. Il contient également un pointeur vers un `CRuntimeClass` qui identifie le type de vue à créer. Les informations de classe d’exécution et le pointeur de document en cours sont utilisés pour créer une nouvelle vue dynamiquement. Le tableau suivant indique comment et quand chaque `CCreateContext` membre peut être utilisé :  
  
|Membre|Type|Il concerne|  
|------------|----------|--------------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` de la nouvelle vue à créer.|  
|`m_pCurrentDoc`|`CDocument*`|Le document existant à associer à la nouvelle vue.|  
|`m_pNewDocTemplate`|`CDocTemplate*`|Le modèle de document associé à la création d’une fenêtre frame MDI.|  
|`m_pLastView`|`CView*`|La vue d’origine sur lequel sont modélisées vues supplémentaires, comme la création d’affichages, la fenêtre fractionnée ou la création d’une seconde vue sur un document.|  
|`m_pCurrentFrame`|`CFrameWnd*`|La fenêtre frame sur lequel sont modélisées fenêtres frames supplémentaires, comme dans la création d’une deuxième fenêtre frame dans un document.|  
  
 Lorsqu’un modèle de document crée un document et ses composants associés, il valide les informations stockées dans le `CCreateContext` structure. Par exemple, une vue ne doit pas être créée pour un document qui n’existe pas.  
  
> [!NOTE]
>  Tous les pointeurs de `CCreateContext` sont facultatives et peuvent être `NULL` si non spécifié ou inconnu.  
  
 `CCreateContext` est utilisé par les fonctions membres répertoriées sous « Voir aussi ». Pour plus d’informations, consultez les descriptions de ces fonctions si vous envisagez de les remplacer.  
  
 Voici quelques directives générales :  
  
-   Lorsqu’est passé comme argument pour la création de la fenêtre, comme dans `CWnd::Create`, `CFrameWnd::Create`, et `CFrameWnd::LoadFrame`, le contexte de créer spécifie ce que la nouvelle fenêtre doit être connectée. Pour la plupart des fenêtres, la structure entière est facultative et un `NULL` pointeur peut être passé.  
  
-   Pour les fonctions membres substituables, tels que `CFrameWnd::OnCreateClient`, `CCreateContext` argument est facultatif.  
  
-   Pour les fonctions membres impliquées dans la vue Création, vous devez fournir suffisamment d’informations pour créer la vue. Par exemple, pour la première vue dans une fenêtre fractionnée, vous devez fournir les informations de classe d’affichage et le document actif.  
  
 En règle générale, si vous utilisez les valeurs par défaut du framework, vous pouvez ignorer `CCreateContext`. Si vous essayez de modifications plus complexes, le code source de bibliothèque Microsoft Foundation Class ou les exemples de programmes, par exemple VIEWEX, vous guide. Si vous ne perdez pas un paramètre obligatoire, une assertion de framework vous indique ce que vous avez oublié.  
  
 Pour plus d’informations sur `CCreateContext`, consultez l’exemple MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxext.h  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)   
 [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)   
 [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)   
 [CSplitterWnd::Create statiques](../../mfc/reference/csplitterwnd-class.md#create)   
 [CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)   
 [CWnd::Create](../../mfc/reference/cwnd-class.md#create)

