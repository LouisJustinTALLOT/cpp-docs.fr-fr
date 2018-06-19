---
title: -MANIFESTINPUT (spécifier l’entrée de manifeste) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eecf1740855c2feef0d7cac4bbcc85ad95eade6f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372849"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Spécifier l'entrée de manifeste)
Spécifie un fichier manifeste d’entrée à inclure dans le manifeste est incorporé dans l’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filename`  
 Le fichier manifeste à inclure dans le manifeste incorporé.  
  
## <a name="remarks"></a>Notes  
 Le **/MANIFESTINPUT** option spécifie le chemin d’accès de fichier d’entrée à utiliser pour créer le manifeste incorporé dans une image exécutable. Si vous avez manifeste plusieurs fichiers d’entrée, utilisez le commutateur plusieurs fois : une fois pour chaque fichier d’entrée. Les fichiers d’entrée de manifeste sont fusionnés pour créer le manifeste incorporé. Cette option requiert le **de manifeste : incorporer** option.  
  
 Cette option ne peut pas être définie directement dans [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. Utilisez plutôt le **des fichiers manifeste supplémentaires** propriété du projet pour spécifier les fichiers manifeste supplémentaires à inclure. Pour plus d’informations, consultez [entrée et sortie, outil manifeste, propriétés de Configuration, \<Projectname > Property Pages Dialog Box](../../ide/input-and-output-manifest-tool.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)