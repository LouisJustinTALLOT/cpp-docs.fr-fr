---
title: Diagnostic affiché par la fonction assert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c219669d018dc8c4cb038e90dffd1137877f422
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382875"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostic imprimé par la fonction d'assertion
**ANSI 4.2** Diagnostic imprimé et comportement d'arrêt de la fonction **assert**  
  
 La fonction **assert** imprime un message de diagnostic et appelle la routine **abort** si l'expression est false (0). Le message de diagnostic se présente sous la forme  
  
 **Échec d’assertion** : *expression***, fichier** *nom_fichier***, ligne** *numéro_ligne*  
  
 où filename est le nom du fichier source et linenumber est le numéro de ligne de l'assertion qui a échoué dans le fichier source. Aucune action n'est effectuée si l'expression est vraie (différente de zéro).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions des bibliothèques](../c-language/library-functions.md)