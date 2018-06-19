---
title: -/LARGEADDRESSAWARE (gérer les longues adresses) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
dev_langs:
- C++
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f81424c49c5d67713cf478f69701c52504cfa8c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372124"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Gérer les longues adresses)
```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 L’option /LARGEADDRESSAWARE indique à l’éditeur de liens que l’application peut gérer des adresses supérieures à 2 gigaoctets. Dans les compilateurs 64 bits, cette option est activée par défaut. Dans les compilateurs 32 bits, / LARGEADDRESSAWARE : no est activée si /LARGEADDRESSAWARE n’est pas spécifiée autrement sur la ligne de l’éditeur de liens.  
  
 Si une application a été liée avec cette option, DUMPBIN [/HEADERS](../../build/reference/headers.md) affiche des informations à cet effet.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **système** page de propriétés.  
  
4.  Modifier la **activation des longues adresses** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)