---
title: Nettoyage des exceptions CString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 656739ad000612f130f5cdfb1a53a6de2d67c4c8
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761366"
---
# <a name="cstring-exception-cleanup"></a>Nettoyage des exceptions CString

Dans les versions précédentes de MFC, il était important de nettoyer [CString](../atl-mfc-shared/reference/cstringt-class.md) objets après utilisation. Avec MFC version 3.0 et versions ultérieure, un nettoyage explicite n’est plus nécessaire.

Sous l’exception C++ mécanisme MFC utilise désormais de gestion, il est inutile à vous soucier de nettoyage après une exception. Pour obtenir une description de la façon C++ « déroule » la pile après une exception est interceptée, consultez [try, catch et throw instructions](../cpp/try-throw-and-catch-statements-cpp.md). Même si vous utilisez la bibliothèque MFC **essayez**/**CATCH** macros au lieu des mots clés C++ **essayez** et **catch**, MFC utilise le C++ mécanisme d’exception en-dessous, donc vous toujours n’avez pas besoin nettoyer explicitement.

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

