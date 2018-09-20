---
title: 'Exceptions : Exceptions dans les constructeurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cab21255698c19046cfca185a0d8d7e7c530112
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421932"
---
# <a name="exceptions-exceptions-in-constructors"></a>Exceptions : exceptions dans les constructeurs

Lorsque vous levez une exception dans un constructeur, nettoyer toutes les allocations de mémoire et les objets que vous avez apportées, comme expliqué dans [Exceptions : levée d’Exceptions à partir de vos propres fonctions](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Lorsque vous levez une exception dans un constructeur, la mémoire pour l’objet lui-même a déjà été allouée au moment où que le constructeur est appelé. Par conséquent, le compilateur automatiquement désalloue la mémoire occupée par l’objet une fois que l’exception est levée.

Pour plus d’informations, consultez [Exceptions : libération d’objets dans les Exceptions](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

