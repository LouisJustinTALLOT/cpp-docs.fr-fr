---
title: 'Procédure : Charger une ressource de ruban à partir d’une Application MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: b7691d4168101209b0e2d2500012a2b4a8e47788
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289553"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Procédure : Charger une ressource de ruban à partir d’une Application MFC

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
