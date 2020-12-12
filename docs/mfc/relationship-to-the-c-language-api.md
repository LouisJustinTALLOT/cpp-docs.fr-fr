---
description: 'En savoir plus sur : relation avec l’API du langage C'
title: Relation avec l'API du langage C
ms.date: 11/04/2016
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: fdfc03d9e8379ee4f19452ce81cba9957930bfe4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218067"
---
# <a name="relationship-to-the-c-language-api"></a>Relation avec l'API du langage C

La caractéristique unique qui définit la bibliothèque MFC (Microsoft Foundation Class), à l’exception des autres bibliothèques de classes pour Windows, est le mappage très étroit de l’API Windows écrite en langage C. En outre, vous pouvez généralement combiner librement les appels à la bibliothèque de classes avec des appels directs à l’API Windows. Toutefois, cet accès direct ne signifie pas que les classes sont entièrement remplacées pour cette API. Les développeurs doivent toujours parfois effectuer des appels directs à certaines fonctions Windows, comme [SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) et [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics), par exemple. Une fonction Windows est encapsulée par une fonction membre de classe uniquement lorsque cela présente un avantage évident.

Étant donné que vous devez parfois effectuer des appels de fonction Windows natifs, vous devez avoir accès à la documentation de l’API Windows en langage C. Cette documentation est fournie avec Microsoft Visual C++.

> [!NOTE]
> Pour obtenir une vue d’ensemble du fonctionnement de l’infrastructure de bibliothèque MFC, consultez [utilisation des classes pour écrire des applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Voir aussi

[Philosophie générale de conception de classes](../mfc/general-class-design-philosophy.md)
