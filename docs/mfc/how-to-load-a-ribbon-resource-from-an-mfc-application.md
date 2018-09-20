---
title: 'Comment : charger une ressource de ruban à partir d’une Application MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1643989a96a9003847fb53de624bff12cd51cd88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434288"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Comment : charger une ressource du ruban à partir d'une application MFC

Pour utiliser la ressource de ruban dans votre application, modifiez l’application pour charger la ressource de ruban.

### <a name="to-load-a-ribbon-resource"></a>Pour charger une ressource de ruban

1. Déclarez le `Ribbon Control` de l’objet dans le `CMainFrame` classe.

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. Dans `CMainFrame::OnCreate`, créer et initialiser le contrôle du ruban.

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>Voir aussi

[Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)

