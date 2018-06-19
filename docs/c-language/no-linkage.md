---
title: Aucune liaison | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc6515020272d19a9b9efca7341293be4983a56
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383785"
---
# <a name="no-linkage"></a>Aucune liaison
Si une déclaration d'un identificateur dans un bloc n'inclut pas le spécificateur de classe de stockage `extern`, l'identificateur n'a aucune liaison et est propre à la fonction.  
  
 Les identificateurs suivants n'ont aucune liaison :  
  
-   Un identificateur déclaré comme autre chose qu'un objet ou une fonction  
  
-   un identificateur déclaré comme étant un paramètre de fonction  
  
-   Un identificateur de portée de bloc pour un objet déclaré sans spécificateur de classe de stockage `extern`  
  
 Si un identificateur n'a aucune liaison, une nouvelle déclaration du même nom (dans un spécificateur de déclarateur ou de type) au même niveau de portée génère une erreur de redéfinition de symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)