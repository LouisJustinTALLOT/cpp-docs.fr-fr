---
description: 'En savoir plus sur : Comment : charger une ressource de ruban à partir d’une application MFC'
title: "Comment : charger une ressource du ruban à partir d'une application MFC"
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 231acbd475bf84b2623eb44f9a3500ab94145d06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330192"
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
