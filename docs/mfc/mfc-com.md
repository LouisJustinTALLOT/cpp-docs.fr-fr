---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: da194510938e3fe02eba5993182e811fdf2e1b7c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618012"
---
# <a name="mfc-com"></a>MFC COM

Un sous-ensemble de MFC est conçu pour prendre en charge COM, tandis que la plupart des Active Template Library (ATL) est conçu pour la programmation COM. Cette section de rubriques décrit la prise en charge de MFC pour COM.

Les technologies actives (telles que les contrôles ActiveX, la relation contenant-contenu de document actif, OLE, etc.) utilisent le modèle COM (Component Object Model) pour permettre aux composants logiciels d’interagir les uns avec les autres dans un environnement en réseau, quelle que soit la langue avec laquelle ils ont été créés. Les technologies actives peuvent être utilisées pour créer des applications qui s’exécutent sur le bureau ou sur Internet. Pour plus d’informations, consultez [Présentation de com](../atl/introduction-to-com.md) ou [du modèle d’objet de composant](/windows/win32/com/the-component-object-model).

Les technologies actives incluent les technologies client et serveur, notamment les suivantes :

- Les contrôles ActiveX sont des objets interactifs qui peuvent être utilisés dans des conteneurs tels qu’un site Web. Pour plus d’informations sur les contrôles ActiveX, consultez :

  - [Contrôles ActiveX MFC](mfc-activex-controls.md)

  - [Contrôles ActiveX sur Internet](activex-controls-on-the-internet.md)

  - [Vue d’ensemble : Internet](mfc-internet-programming-basics.md)

  - [Mettre à niveau un contrôle ActiveX existant à utiliser sur Internet](upgrading-an-existing-activex-control.md)

  - [Débogage d’un contrôle ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Active Scripting contrôle le comportement intégré d’un ou de plusieurs contrôles ActiveX à partir d’un navigateur ou d’un serveur. Pour plus d’informations sur Active Scripting, consultez [technologie active sur Internet](active-technology-on-the-internet.md).

- [Automation](automation.md) (anciennement appelé OLE Automation) permet à une application de manipuler des objets implémentés dans une autre application, ou d’exposer des objets pour qu’ils puissent être manipulés.

   L’objet automatisé peut être local ou distant (sur un autre ordinateur accessible via un réseau). Automation est disponible pour les objets OLE et COM.

- Cette section fournit également des informations sur la façon d’écrire des composants COM à l’aide de MFC, par exemple, dans des [points de connexion](connection-points.md).

Pour plus d’informations sur ce qui est toujours appelé OLE par rapport à ce qui est maintenant appelé technologie active, consultez les rubriques relatives à [OLE](ole-in-mfc.md).

## <a name="in-this-section"></a>Dans cette section

[Documents actifs (contenance)](active-document-containment.md)

[Automation](automation.md)

[Points de connexion](connection-points.md)

[Contrôles ActiveX MFC](mfc-activex-controls.md)

## <a name="see-also"></a>Voir aussi

[Concepts](mfc-concepts.md)
