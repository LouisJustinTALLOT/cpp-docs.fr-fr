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
ms.openlocfilehash: 514251475050e728be1959417ead1dbdf96e4800
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358195"
---
# <a name="mfc-com"></a>MFC COM

Un sous-ensemble de MFC est conçu pour prendre en charge COM, tandis que la plupart de la bibliothèque Active Template (ATL) est conçu pour la programmation COM. Cette section de sujets décrit le soutien de MFC pour COM.

Les technologies actives (telles que les contrôles ActiveX, le confinement actif des documents, l’OL, etc.) utilisent le modèle d’objet composant (COM) pour permettre aux composants logiciels d’interagir les uns avec les autres dans un environnement en réseau, quelle que soit la langue avec laquelle ils ont été créés. Les technologies actives peuvent être utilisées pour créer des applications qui s’exécutent sur le bureau ou sur Internet. Pour plus d’informations voir [Introduction to COM](../atl/introduction-to-com.md) ou The Component Object [Model](/windows/win32/com/the-component-object-model).

Les technologies actives comprennent les technologies client et serveur, y compris les suivantes :

- Les commandes ActiveX sont des objets interactifs qui peuvent être utilisés dans des conteneurs tels qu’un site Web. Pour plus d’informations sur les contrôles ActiveX, voir :

  - [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

  - [Contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md)

  - [Aperçu: Internet](../mfc/mfc-internet-programming-basics.md)

  - [Mettre à niveau un contrôle ActiveX existant à utiliser sur Internet](../mfc/upgrading-an-existing-activex-control.md)

  - [Déboguer un contrôle ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Le script actif contrôle le comportement intégré d’un ou plusieurs contrôles ActiveX à partir d’un navigateur ou d’un serveur. Pour plus d’informations sur le script actif, voir [Active Technology sur Internet](../mfc/active-technology-on-the-internet.md).

- [L’automatisation](../mfc/automation.md) (anciennement connue sous le nom d’OLE Automation) permet à une application de manipuler des objets implémentés dans une autre application, ou d'«exposer» des objets afin qu’ils puissent être manipulés.

   L’objet automatisé peut être local ou distant (sur une autre machine accessible sur un réseau). Automation est disponible pour les objets OLE et COM.

- Cette section fournit également des informations sur la façon d’écrire des composants COM en utilisant MFC, par exemple, dans [les points de connexion](../mfc/connection-points.md).

Pour une discussion de ce qu’on appelle encore OLE par rapport à ce qu’on appelle maintenant la technologie active, voir les sujets sur [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>Dans cette section

[Documents actifs (contenance)](../mfc/active-document-containment.md)

[Automation](../mfc/automation.md)

[Points de connexion](../mfc/connection-points.md)

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Voir aussi

[Concepts liés à la](../mfc/mfc-concepts.md)
