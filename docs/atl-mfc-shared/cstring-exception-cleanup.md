---
title: Nettoyage des exceptions CString
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: d131ce8ebe5158d7f3a567580064068742b63707
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236626"
---
# <a name="cstring-exception-cleanup"></a>Nettoyage des exceptions CString

Dans les versions précédentes de MFC, il était important de nettoyer [CString](../atl-mfc-shared/reference/cstringt-class.md) objets après utilisation. Avec MFC version 3.0 et versions ultérieure, un nettoyage explicite n’est plus nécessaire.

Sous l’exception C++ mécanisme MFC utilise désormais de gestion, il est inutile à vous soucier de nettoyage après une exception. Pour obtenir une description de la façon C++ « déroule » la pile après une exception est interceptée, consultez [try, catch et throw instructions](../cpp/try-throw-and-catch-statements-cpp.md). Même si vous utilisez la bibliothèque MFC **essayez**/**CATCH** macros au lieu des mots clés C++ **essayez** et **catch**, MFC utilise le C++ mécanisme d’exception en-dessous, donc vous toujours n’avez pas besoin nettoyer explicitement.

## <a name="see-also"></a>Voir aussi

[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
