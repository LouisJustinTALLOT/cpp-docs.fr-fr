---
title: Unicode et MBCS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e10c07e11cbe940b5f7cfee460ddd33f6f5ff1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857348"
---
# <a name="unicode-and-mbcs"></a>Unicode et MBCS
La bibliothèque Microsoft Foundation Classes (MFC), la bibliothèque Runtime C pour Visual C++ et l’environnement de développement Visual C++ sont activées pour faciliter la programmation internationale. Ils fournissent :  
  
-   Prise en charge de la norme Unicode sous Windows. Unicode est la norme actuelle et doit être utilisé chaque fois que possible.  
  
     Unicode est un caractère de 16 bits de codage, permettant le codage pour toutes les langues. Tous les caractères ASCII sont inclus dans Unicode en tant que caractères élargis.  
  
-   Prise en charge pour un formulaire de jeu de caractères multioctets (MBCS) appelé jeu de caractères de codés sur deux octets (DBCS) sur toutes les plateformes.  
  
     Les caractères DBCS sont composés de 1 ou 2 octets. Certaines plages d’octets sont définis pour une utilisation en tant qu’octets de tête. Un octet de tête indique qu’il et l’octet de fin suivante comprennent un caractère unique de 2 octets. Vous devez conserver le suivi des octets d’octets de tête. Dans un jeu de caractères multioctets, les octets de tête sont compris dans une plage et les octets de fin dans une autre. Lorsque ces plages se chevauchent, il peut être nécessaire d’évaluer le contexte pour déterminer si un octet donné fonctionne comme un octet de tête ou un octet de fin.  
  
-   Prise en charge des outils qui simplifient la programmation MBCS des applications écrites pour les marchés internationaux.  
  
     Sur une version compatible MBCS du système d’exploitation Windows, le système de développement Visual C++, y compris l’éditeur de code source intégré, débogueur et les outils de ligne de commande, est totalement compatible MBCS. Pour plus d’informations, consultez [prise en charge MBCS dans Visual C++](../text/mbcs-support-in-visual-cpp.md).  
  
> [!NOTE]
>  Dans cette documentation, MBCS est utilisé pour décrire la prise en charge de tous les non-Unicode de caractères multioctets. Dans Visual C++, MBCS signifie toujours DBCS. Jeux de caractères plus large que 2 octets ne sont pas pris en charge.  
  
 Par définition, le jeu de caractères ASCII est un sous-ensemble de tous les jeux de caractères multioctets. Dans de nombreux jeux de caractères multioctets, chaque caractère de la plage 0x00-0x7F est identique au caractère qui a la même valeur dans le jeu de caractères ASCII. Par exemple, dans les chaînes de caractères ASCII et MBCS, 1 octet **NULL** caractère ('\0') a la valeur 0 x 00 et indique le caractère null de fin.  
  
## <a name="see-also"></a>Voir aussi  
 [Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)   
 [Compatibilité internationale](../text/international-enabling.md)