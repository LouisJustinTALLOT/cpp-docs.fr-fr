---
title: 'Exceptions : Levée d’Exceptions à partir de vos propres fonctions | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dae6f2c0d1cab021cc91854a34f10423a1122dec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346192"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Exceptions : levée d'exceptions à partir de vos propres fonctions
Il est possible d’utiliser le paradigme de gestion des exceptions MFC uniquement pour intercepter les exceptions levées par les fonctions dans MFC ou d’autres bibliothèques. En plus d’intercepter les exceptions levées par le code de bibliothèque, vous pouvez lever des exceptions à partir de votre propre code si vous écrivez des fonctions qui peuvent rencontrer des conditions exceptionnelles.  
  
 Lorsqu’une exception est levée, l’exécution de la fonction en cours est arrêtée et accède directement à la **catch** bloc de l’image de l’exception la plus intérieure. Le mécanisme d’exception ignore le chemin d’accès de la sortie normale d’une fonction. Par conséquent, vous devez veillez à supprimer ces blocs de mémoire qui seraient supprimés dans une sortie normale.  
  
#### <a name="to-throw-an-exception"></a>Pour lever une exception  
  
1.  Utilisez une des fonctions d’assistance MFC, telles que `AfxThrowMemoryException`. Ces fonctions lèvent un objet exception préalloué du type approprié.  
  
     Dans l’exemple suivant, une fonction essaie d’allouer deux blocs de mémoire et lève une exception si l’allocation échoue :  
  
     [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]  
  
     Si la première allocation échoue, vous pouvez simplement lever l’exception de mémoire. Si la première allocation réussit mais que la deuxième échoue, vous devez libérer le premier bloc d’allocation avant de lever l’exception. Si les deux allocations réussissent, vous pouvez poursuivre normalement et libérer les blocs en quittant la fonction.  
  
     - ou  
  
2.  Une exception définie par l’utilisateur permet d’indiquer un problème. Vous pouvez lever un élément de n’importe quel type, voire une classe entière, comme votre exception.  
  
     L’exemple suivant tente d’émettre un signal sonore via un périphérique audio et lève une exception en cas de panne.  
  
     [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]  
  
> [!NOTE]
>  De MFC gestion par défaut des exceptions s’applique uniquement à des pointeurs vers `CException` objets (et les objets de `CException`-classes dérivées). L’exemple ci-dessus ignore le mécanisme d’exception MFC.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

