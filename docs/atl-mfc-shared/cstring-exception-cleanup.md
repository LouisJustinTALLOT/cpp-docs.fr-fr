---
title: Nettoyage des exceptions CString | Documents Microsoft
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
ms.openlocfilehash: d18d10d517a6c5b0d075a7fb0ed113448625b698
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355504"
---
# <a name="cstring-exception-cleanup"></a>Nettoyage des exceptions CString
Dans les versions précédentes de MFC, il était important d’éliminer les [CString](../atl-mfc-shared/reference/cstringt-class.md) objets après utilisation. Avec MFC version 3.0 et versions ultérieure, un nettoyage explicite n’est plus nécessaire.  
  
 Sous l’exception C++ mécanisme MFC utilise désormais de gestion, il est inutile à vous soucier de nettoyage après une exception. Pour obtenir une description de la manière C++ « déroule » la pile après une exception est interceptée, consultez [try, catch et throw instructions](../cpp/try-throw-and-catch-statements-cpp.md). Même si vous utilisez la bibliothèque MFC **essayez**/**CATCH** macros au lieu des mots clés C++ **essayez** et **catch**, MFC utilise C++ mécanisme d’exception sous, donc vous toujours n’avez pas besoin nettoyer explicitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

