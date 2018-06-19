---
title: /APPCONTAINER (application de Store UWP/Microsoft) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca1a3ed5adaada689d374eeb3e67bae6c989e0b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369290"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER (application de la banque Microsoft)
Spécifie si l’éditeur de liens crée une image exécutable qui doit être exécutée dans un conteneur d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, /APPCONTAINER est désactivée.  
  
 Cette option modifie un fichier exécutable pour indiquer si l’application doit être exécutée dans l’environnement d’isolation des processus appcontainer. Spécifiez /APPCONTAINER pour une application qui doit s’exécuter dans l’environnement appcontainer — par exemple, une application 8.x plateforme Windows universelle (UWP) ou Windows Phone. (L’option est définie automatiquement dans Visual Studio lorsque vous créez une application Windows universelle à partir d’un modèle.) Pour une application de bureau, spécifiez /APPCONTAINER:NO ou omettez simplement l’option.  
  
 L’option /APPCONTAINER a été introduite dans [!INCLUDE[win8](../../build/reference/includes/win8_md.md)].  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration** nœud.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **ligne de commande** page de propriétés.  
  
5.  Dans **des Options supplémentaires**, entrez `/APPCONTAINER` ou `/APPCONTAINER:NO`.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)