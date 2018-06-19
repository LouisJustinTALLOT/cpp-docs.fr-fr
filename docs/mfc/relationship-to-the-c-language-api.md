---
title: Relation avec l’API en langage C | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d06c4adfa5493929a24c233fa923451c7bf0f95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379227"
---
# <a name="relationship-to-the-c-language-api"></a>Relation avec l'API du langage C
Si la caractéristique unique qui définit la bibliothèque Microsoft Foundation classes (MFC) indépendamment des autres bibliothèques de classes pour Windows est le mappage très proche de l’API Windows écrites en langage C. En outre, vous pouvez combiner généralement des appels à la bibliothèque de classes librement avec des appels directs à l’API Windows. Cet accès direct n’implique pas, toutefois, que les classes sont un remplacement complet pour cette API. Les développeurs doivent néanmoins occasionnellement effectuer des appels directs à certaines fonctions de Windows, tel que [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) et [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385), par exemple. Une fonction de Windows est encapsulée par une fonction membre de classe uniquement s’il existe un avantage à cet effet.  
  
 Car vous devrez parfois effectuer des appels de fonction Windows natives, vous devriez avoir accès à la documentation de l’API de Windows en langage C. Cette documentation est incluse dans Microsoft Visual C++.  
  
> [!NOTE]
>  Pour une vue d’ensemble du fonctionne de l’infrastructure de la bibliothèque MFC, consultez [l’utilisation des Classes pour l’écriture d’Applications Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Philosophie générale de conception des classes](../mfc/general-class-design-philosophy.md)
