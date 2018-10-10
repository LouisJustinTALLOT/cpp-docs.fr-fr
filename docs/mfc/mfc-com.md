---
title: MFC COM | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC COM (MFC)
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 660b2fc2f6ece6f60ff7bd1868b3a65bc8f045c1
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890034"
---
# <a name="mfc-com"></a>MFC COM

Un sous-ensemble de MFC est conçu pour prendre en charge COM, alors que la plupart de la bibliothèque ATL (Active Template) est conçu pour la programmation COM. Cette section décrit la prise en charge de MFC pour COM.

Les technologies actives (telles que ActiveX des contrôles, relation contenant-contenu de document actif, OLE et ainsi de suite) utilisent le composant COM (Object Model) pour activer les composants logiciels interagir avec eux dans un environnement réseau, quel que soit le langage avec lequel ils ont été créé. Technologies actives peuvent être utilisées pour créer des applications qui s’exécutent sur le bureau ou sur Internet. Pour plus d’informations, consultez [Introduction à COM](../atl/introduction-to-com.md) ou [le modèle d’objet composant](/windows/desktop/com/the-component-object-model).

Technologies Active incluent des technologies client et serveur, notamment les suivantes :

- Contrôles ActiveX sont des objets interactifs qui peuvent être utilisées dans des conteneurs, tel qu’un site Web. Pour plus d’informations sur les contrôles ActiveX, consultez :

   - [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

   - [Contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md)

   - [Vue d’ensemble : Internet](../mfc/mfc-internet-programming-basics.md)

   - [Mise à niveau d’un contrôle ActiveX à utiliser sur Internet](../mfc/upgrading-an-existing-activex-control.md)

   - [Débogage d’un contrôle ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Active scripting contrôle le comportement intégré d’un ou plusieurs contrôles ActiveX à partir d’un navigateur ou un serveur. Pour plus d’informations sur les scripts active, consultez [technologie Active sur Internet](../mfc/active-technology-on-the-internet.md).

- [Automation](../mfc/automation.md) (anciennement appelé OLE Automation) permet à une application de manipuler des objets implémentés dans une autre application, ou « exposer » les objets afin qu’ils puissent être manipulés.

     L’objet automatisé peut être local ou distant (sur un autre ordinateur accessible via un réseau). Automation est disponible pour les objets OLE et COM.

- Cette section fournit également des informations sur la façon d’écrire des composants COM à l’aide de MFC, par exemple, dans [Points de connexion](../mfc/connection-points.md).

Pour une description de ce qui est toujours nommé OLE par rapport à ce que l'on appelle maintenant la technologie active, consultez les rubriques sur [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>Dans cette section

[Documents actifs (contenance)](../mfc/active-document-containment.md)

[Automation](../mfc/automation.md)

[Points de connexion](../mfc/connection-points.md)

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)

