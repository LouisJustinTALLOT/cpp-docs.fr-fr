---
title: Développement des caractères génériques | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb58d5da479d686cac0d18c9d36e500bd6b5a632
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420644"
---
# <a name="wildcard-expansion"></a>Développement des caractères génériques
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Vous pouvez utiliser des caractères génériques (le point d’interrogation (?) et l’astérisque (*)) pour spécifier des arguments de nom de fichier et de chemin d’accès sur la ligne de commande.  
  
 Arguments de ligne de commande sont gérés par une routine appelée **_setargv** (ou **_wsetargv** dans l’environnement à caractères larges), qui par défaut ne développe pas les caractères génériques en chaînes séparées dans le `argv`tableau de chaînes. Pour plus d’informations sur l’activation du développement des caractères génériques, consultez [développement les Arguments génériques](../c-language/expanding-wildcard-arguments.md).  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [main : démarrage du programme](../cpp/main-program-startup.md)