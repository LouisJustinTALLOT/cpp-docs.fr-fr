---
title: STUB | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: STUB
dev_langs: C++
helpviewer_keywords: STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 27d7ee77d527e8d8715d182609f1cb847b10a3d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="stub"></a>STUB
Lorsqu’il est utilisé dans un fichier de définition de module qui génère un pilote de périphérique virtuel (VxD), vous permet de spécifier un nom de fichier qui contient une structure IMAGE_DOS_HEADER (définie dans WINNT. H) à utiliser dans le pilote de périphérique virtuel (VxD), au lieu de l’en-tête par défaut.  
  
```  
STUB:filename  
```  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez spécifier *nom de fichier* avec la [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) option de l’éditeur de liens.  
  
 STUB est valide dans un fichier de définition de module uniquement lors de la génération d’un pilote VxD.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)