---
title: Documenter et affichage de Classes créées par l’Assistant Application MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b83886784970492da0c5e2a335dbe08119ecaae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349920"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Classes de document et de vue créées par l'Assistant Application MFC
L’Assistant Application MFC vous donne un coup de développement de votre programme en créant des documents squelette et des classes d’affichage pour vous. Vous pouvez ensuite [mapper les commandes et les messages à ces classes](../mfc/reference/mapping-messages-to-functions.md) et utiliser l’éditeur de code source Visual C++ pour écrire leurs fonctions membres.  
  
 La classe de document créée par l’Assistant Application MFC est dérivée de la classe [CDocument](../mfc/reference/cdocument-class.md). La classe d’affichage est dérivée [CView](../mfc/reference/cview-class.md). Les noms que l’Assistant Application attribue à ces classes et les fichiers qui contiennent les sont basées sur le nom du projet que vous indiquez dans la boîte de dialogue Assistant Création d’applications. Dans l’Assistant Application, vous pouvez utiliser la page Classes générées pour modifier les noms par défaut.  
  
 Certaines applications sont peut-être plus d’une classe de document, classe d’affichage ou classe de fenêtre frame. Pour plus d’informations, consultez [plusieurs Types de documents, vues et fenêtres Frame](../mfc/multiple-document-types-views-and-frame-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture document/vue](../mfc/document-view-architecture.md)

