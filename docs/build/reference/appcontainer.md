---
title: -APPCONTAINER | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea6f08a141d48183d96dba6cb02fcf31909af0ae
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686251"
---
# <a name="appcontainer"></a>/APPCONTAINER
Marque un fichier exécutable qui doit s’exécuter dans un conteneur d’application, par exemple, une application Microsoft Store ou Windows universelles.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 Un fichier exécutable dont l’option **/APPCONTAINER** est définie ne peut être exécuté que dans un conteneur d’application, ce qui correspond à l’environnement d’isolation des processus introduit dans Windows 8. Pour les applications Microsoft Store et Windows universelles, cette option doit être définie.  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)   
 [Qu’est une application Windows universelle ?](/windows/uwp/get-started/universal-application-platform-guide)