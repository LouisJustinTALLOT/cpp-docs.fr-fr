---
title: "Comment : charger une ressource du ruban à partir d'une application MFC"
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 14ba37952d6f8849c51b36901a6bc17404f938e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515152"
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

