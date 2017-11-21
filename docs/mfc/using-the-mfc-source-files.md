---
title: "À l’aide de la bibliothèque MFC des fichiers sources | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 342c687ad992b6c587ea7518811e43bcca9db6b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="using-the-mfc-source-files"></a>Utilisation des fichiers sources MFC
La bibliothèque Microsoft Foundation classes (MFC) fournit le code source complet. Fichiers d’en-tête (.h) se trouvent dans le répertoire \atlmfc\include ; fichiers d’implémentation (.cpp) se trouvent dans le répertoire \atlmfc\src\mfc.  
  
 Cette famille d’articles explique les conventions utilisées par MFC pour commenter les différentes parties de chaque classe, ce que signifient ces commentaires et ce que vous attendre à trouver dans chaque section. Les Assistants Visual C++ utilisent des conventions similaires pour les classes qu’il crée pour vous, et vous constaterez probablement ces conventions utiles pour votre propre code.  
  
 Vous connaissez peut-être le **public**, `protected`, et `private` mots clés C++. En examinant les fichiers d’en-tête MFC, vous constaterez que chaque classe peut avoir plusieurs de chacune d’elles. Par exemple, les fonctions et variables de membre public peuvent être sous plusieurs **public** (mot clé). Il s’agit, car MFC sépare les variables membres et les fonctions basées sur leur utilisation, et non par le type d’accès autorisé. MFC utilise `private` avec parcimonie ; y compris les éléments pris en compte les détails d’implémentation sont généralement protégés et très souvent publics. Bien que l’accès aux détails d’implémentation n’est pas recommandée, MFC laisse la décision pour vous.  
  
 Dans les fichiers sources MFC et les fichiers créés par l’Assistant Application MFC, vous trouverez des commentaires comme celles-ci dans les déclarations de classe (généralement dans cet ordre) :  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 Les sujets abordés dans cette famille d’articles sont les suivantes :  
  
-   [Un exemple des commentaires](../mfc/an-example-of-the-comments.md)  
  
-   [La / / implémentation de commentaire](../mfc/decrement-implementation-comment.md)  
  
-   [La / / constructeurs (commentaire)](../mfc/decrement-constructors-comment.md)  
  
-   [La / / commentaire d’attributs](../mfc/decrement-attributes-comment.md)  
  
-   [La / / opérations comment](../mfc/decrement-operations-comment.md)  
  
-   [La / / remplaçable commentaire](../mfc/decrement-overridables-comment.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)

