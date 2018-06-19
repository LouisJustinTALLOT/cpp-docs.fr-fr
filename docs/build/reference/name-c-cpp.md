---
title: NOM (C/C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94b82a65cf68d9802d7bf9620e4128ab6b35071
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371812"
---
# <a name="name-cc"></a>NAME (C/C++)
Spécifie un nom pour le fichier de sortie principal.  
  
```  
NAME [application][BASE=address]  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier un nom de fichier de sortie est le [/OUT](../../build/reference/out-output-file-name.md) option de l’éditeur de liens et pour définir l’adresse de base d’une manière équivalente est le [/BASE](../../build/reference/base-base-address.md) option de l’éditeur de liens. Si les deux sont spécifiées, les remplacements **nom**.  
  
 Si vous générez une DLL, le nom n’affecte que le nom de la DLL.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)