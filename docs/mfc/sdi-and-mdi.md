---
title: SDI et MDI | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db63efe8d7e2622610bb56f5e6885b72b705093b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385802"
---
# <a name="sdi-and-mdi"></a>SDI et MDI
MFC facilite le travail avec l’interface monodocument (SDI) et applications d’interface multidocument (MDI).  
  
 Les applications SDI n'autorisent qu’une seule fenêtre frame de document ouvert à la fois. Les applications MDI permettent plusieurs documents ouverts dans la même instance d’une application de fenêtres frame. Une application MDI possède une fenêtre dans le multiples MDI des fenêtres enfants, qui sont elles-mêmes des fenêtres frame, peuvent être ouverts, chacune contenant un document distinct. Dans certaines applications, les fenêtres enfants peuvent être de types différents, tels que le graphique et les fenêtres de feuille de calcul. Dans ce cas, la barre de menus permettre modifier comme fenêtres enfants MDI de types différents sont activées.  
  
> [!NOTE]
>  Sous Windows 95 et versions ultérieures, les applications sont généralement SDI, car le système d’exploitation a adopté un affichage « centré sur le document ».  
  
 Pour plus d’informations, consultez [Documents, vues et l’infrastructure](../mfc/documents-views-and-the-framework.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
