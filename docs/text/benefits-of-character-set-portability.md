---
title: Avantages du caractère d’un jeu portabilité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1b78048baebfd89aed0ccc898c2bb9e3612525
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853815"
---
# <a name="benefits-of-character-set-portability"></a>Avantages de la portabilité d'un jeu de caractères
Vous pouvez bénéficier de l’aide des fonctionnalités de portabilité runtime MFC et C même si vous n’envisagez pas internationaliser votre application pour :  
  
-   Le codage portable rend votre code base flexible. Vous pouvez ultérieurement le déplacer facilement en Unicode ou MBCS.  
  
-   L’utilisation de Unicode rend vos applications pour Windows est plus efficace. Étant donné que Windows utilise Unicode, les chaînes non-Unicode passés à et depuis le système d’exploitation doivent être traduites, ce qui entraîne une surcharge.  

  
## <a name="see-also"></a>Voir aussi  
 [Unicode et MBCS](../text/unicode-and-mbcs.md)   
 [Prise en charge pour Unicode](../text/support-for-unicode.md)