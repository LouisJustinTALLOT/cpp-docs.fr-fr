---
title: "Comment : charger une ressource du ruban à partir d'une application MFC"
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 47a3b94bbcb14c6c2923524db1f6a83b687e50e8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626402"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Comment : charger une ressource du ruban à partir d'une application MFC

Pour utiliser la ressource de ruban dans votre application, modifiez l’application pour charger la ressource de ruban.

### <a name="to-load-a-ribbon-resource"></a>Pour charger une ressource de ruban

1. Déclarez l' `Ribbon Control` objet dans la `CMainFrame` classe.

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. Dans `CMainFrame::OnCreate` , créez et initialisez le contrôle de ruban.

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

[Concepteur de ruban (MFC)](ribbon-designer-mfc.md)
