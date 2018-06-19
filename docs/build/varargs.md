---
title: Varargs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7b71cd426bc89570f9d394f3e38dc7a002f6e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380506"
---
# <a name="varargs"></a>Varargs
Si des paramètres sont passés via varargs (par exemple, les arguments de points de suspension), essentiellement le passage de paramètres normal s’applique notamment déversement les arguments de la cinquième et ultérieures. Il incombe à nouveau l’appelé aux arguments de vidage qui ont leur adresse. Pour les valeurs à virgule flottante, l’entier et le Registre à virgule flottante contiendra la valeur float si l’appelé attend la valeur dans les registres d’entiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Convention d’appel](../build/calling-convention.md)