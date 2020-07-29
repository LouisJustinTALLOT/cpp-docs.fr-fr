---
title: Nettoyage des exceptions CString
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: 48c8f1c0040236a4f7bf27a2d5ad985ae343c03a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222054"
---
# <a name="cstring-exception-cleanup"></a>Nettoyage des exceptions CString

Dans les versions précédentes de MFC, il était important de nettoyer les objets [CString](../atl-mfc-shared/reference/cstringt-class.md) après utilisation. Avec MFC version 3,0 et versions ultérieures, le nettoyage explicite n’est plus nécessaire.

Dans le cadre du mécanisme de gestion des exceptions C++ que MFC utilise, vous n’avez pas à vous soucier du nettoyage après une exception. Pour obtenir une description de la façon dont C++ « déroule » la pile après l’interception d’une exception, consultez [les instructions Try, catch et Throw](../cpp/try-throw-and-catch-statements-cpp.md). Même si vous utilisez les macros **try** / **catch** de MFC au lieu des mots clés c++ **`try`** et que **`catch`** MFC utilise le mécanisme d’exceptions c++, il n’est pas nécessaire de procéder à un nettoyage explicite.

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
