---
title: -WINMDDELAYSIGN (signer partiellement un winmd) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs:
- C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c50480fae1f4f3e7421236615d059a642d1074f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375556"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (signer partiellement un winmd)
Permet que signature partielle d’un fichier de métadonnées Windows Runtime (.winmd) en plaçant la clé publique dans le fichier.  
  
```  
/WINMDDELAYSIGN[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 Ressemble à la [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) option de l’éditeur de liens qui est appliquée dans le fichier .winmd. Utilisez **/WINMDDELAYSIGN** si vous souhaitez placer uniquement la clé publique dans le fichier .winmd. Par défaut, l’éditeur de liens agit comme si **/winmddelaysign : no** ont été spécifiées ; autrement dit, il ne signe pas le fichier winmd.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **l’éditeur de liens** dossier.  
  
3.  Sélectionnez le **métadonnées Windows** page de propriétés.  
  
4.  Dans le **temporiser la signature de métadonnées Windows** liste déroulante, sélectionnez l’option souhaitée.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)