---
title: Relation avec l’API de langage C | Microsoft Docs
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
ms.openlocfilehash: 8d0bb7aa4f647ceeb61c20cccd626d9da999b241
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200110"
---
# <a name="relationship-to-the-c-language-api"></a>Relation avec l'API du langage C
Cette caractéristique unique qui différencie des autres bibliothèques de classes pour Windows dans la bibliothèque Microsoft Foundation classes (MFC) est le mappage très proche à l’API Windows écrits en langage C. En outre, vous pouvez généralement mélanger les appels à la bibliothèque de classes de librement avec des appels directs à l’API Windows. Cet accès direct n’implique pas, toutefois, que les classes sont un remplacement complet pour cette API. Les développeurs doivent se néanmoins occasionnellement les appels directs à certaines fonctions de Windows, tel que [SetCursor](/windows/desktop/api/winuser/nf-winuser-setcursor) et [GetSystemMetrics](https://msdn.microsoft.com/library/windows/desktop/ms724385), par exemple. Une fonction de Windows est encapsulée par une fonction membre de classe uniquement s’il existe un avantage NET à cet effet.  
  
 Étant donné que vous devez parfois effectuer des appels de fonction Windows natives, vous devez avoir accès à la documentation de l’API de Windows en langage C. Cette documentation est incluse dans Microsoft Visual C++.  
  
> [!NOTE]
>  Pour une vue d’ensemble du fonctionne de l’infrastructure de la bibliothèque MFC, consultez [utilisation des Classes pour écrire des Applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Philosophie générale de conception des classes](../mfc/general-class-design-philosophy.md)
