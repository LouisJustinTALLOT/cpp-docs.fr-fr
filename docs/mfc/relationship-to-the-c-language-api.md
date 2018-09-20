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
ms.openlocfilehash: 027a14213f173bdc6be5fc34e9fd4faf0eba8023
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415147"
---
# <a name="relationship-to-the-c-language-api"></a>Relation avec l'API du langage C

Cette caractéristique unique qui différencie des autres bibliothèques de classes pour Windows dans la bibliothèque Microsoft Foundation classes (MFC) est le mappage très proche à l’API Windows écrits en langage C. En outre, vous pouvez généralement mélanger les appels à la bibliothèque de classes de librement avec des appels directs à l’API Windows. Cet accès direct n’implique pas, toutefois, que les classes sont un remplacement complet pour cette API. Les développeurs doivent se néanmoins occasionnellement les appels directs à certaines fonctions de Windows, tel que [SetCursor](/windows/desktop/api/winuser/nf-winuser-setcursor) et [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics), par exemple. Une fonction de Windows est encapsulée par une fonction membre de classe uniquement s’il existe un avantage NET à cet effet.

Étant donné que vous devez parfois effectuer des appels de fonction Windows natives, vous devez avoir accès à la documentation de l’API de Windows en langage C. Cette documentation est incluse dans Microsoft Visual C++.

> [!NOTE]
>  Pour une vue d’ensemble du fonctionne de l’infrastructure de la bibliothèque MFC, consultez [utilisation des Classes pour écrire des Applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Voir aussi

[Philosophie générale de conception des classes](../mfc/general-class-design-philosophy.md)
